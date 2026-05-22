These files are the intermediate results while converting the Scott Free adventure files into GRIF format.

The sections are:

Game values
Raw command data
Verbs and nouns
Rooms with descriptions and exits
Messages
Items with locations and descriptions
More game values
Expanded command data with comments, pseudocode, and room/item/message text.

The expanded command data is designed to be more readable. For example:

Cmd  40 |    10    38 |    2  13   2  12   0   0   0   0   0   0 |   12   0   0   0 |
            get   che | IF HERE(13="Treasure chest")
                      | IF HERE(12="Wicked looking pirate")
                      | MESSAGE 12="Pirate won't let me"

This runs if you type the command "get chest" (verb 10, noun 38).
It checks the conditions "2 13" = IF HERE(13="Treasure chest") and "2 12" = IF HERE(12="Wicked looking pirate").
If both are true, it runs "12" = MESSAGE 12="Pirate won't let me"
If either are not true, it will continue looking for another command "get chest" = "10, 38" to see if that has all true conditions.

In GRIF, all of the "get chest" commands are merged together, like this:

command.10.38
	@comment("Cmd 40 - get che")
	@if @here(13) @and @here(12) @then
		@msg(message.12)
		@comment("...continued into Cmd 41")
	@elseif @here(13) @and @not @here(12) @then
		@take(13)
		@msg(message.64)
		@comment("...continued into Cmd 159")
	@elseif @herecarry(28) @then
		@take(28)
		@msg(message.64)
	@endif

Some commands run a percentage of the time, such as this one. When the verb = 0, the noun is used as a percentage.

Cmd   3 |     0     3 |    3  24   0   0   0   0   0   0   0   0 |  104 112   0   0 | PARROT PIECES 8
                   3% | IF HERECARRY(24="Parrot")
                      | MESSAGE 54="The Parrot crys:"
                      | MESSAGE 62="`Pieces of eight`"

This says that 3% of the time at the end of each move, if the parrot is here, it will cry "Pieces of eight".
Message numbers over 50 have 50 added the actual number, so message 54 is the value 104 on the right.

In GRIF, these percentage commands are converted into "background" commands.
The background commands all run at the end of each move.
They don't have to be percentages and can be any kind of code.

background.3
	@if @rand(3) @and @herecarry(24) @then
		@comment("PARROT PIECES 8")
		@msg(message.54)
		@msg(message.62)
	@endif
