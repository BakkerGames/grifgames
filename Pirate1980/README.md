## Scott Adams' Pirate's Adventure port to GRIF

This is a port of the Scott Adams game `Pirate's Adventure` to GRIF (Game Runner for Interactive Fiction).

Specifically, the original source comes from the December 1980 BYTE Magazine article by the author about the game, starting on page 192. It provided the entire TRS-80 Level II BASIC source code, designed to run on a TRS-80 with 16K of memory. The source code was in three parts: the game interpreter, a block of DATA statements, and the code to save and load the data to/from a cassette tape. The block of data had values such as descriptions, vocabulary, room exits, and the commands to execute when specific verbs or verb/nouns were entered.

This is a port of that source listing to GRIF. The GRIF interpreter is very similar conceptually to that original game code, reading a text data file containing values to be used and scripts to be executed. Most of this "Pirate1980.grif" file is directly converted from that original DATA block.

To run, get the proper version of "grif.exe" or "grif" for your system. Put it into the same directory as "Pirate1980.grif". In a console/terminal window, run the command "grif.exe Pirate1980.grif" or "./grif Pirate1980.grif".

The full source to GRIF is available at [GRIF](https://github.com/BakkerGames/GRIF). Various Windows and Linux executables are available at [Releases](https://github.com/BakkerGames/GRIF/releases). Source and executables are also available at the [Interactive Fiction Archive](https://www.ifarchive.org/indexes/if-archive/programming/grif/). Games using the GRIF interpreter can be found at [Games](https://www.ifarchive.org/indexes/if-archive/games/grif/).

The original Scott Adams game `Pirate's Adventure` is copyright by Scott and Alexis Adams. The December 1980 BYTE article can be viewed at [Internet Archive](https://archive.org/details/byte-magazine-1980-12/page/n193/mode/2up).