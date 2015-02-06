# Vagrantfile for DFHack
This file will help you build an image based on 23 bit Ubuntu 14.04 and build the latest DFHack code. Simply put the file in a directory and run `vagrant up`. It will automatically install required dependencies and move the code to the current directory (the shared directory). Switch to the dfhack directory and rsync the code to your Dwarf Fortress directory with `rsync -av * <df directory>`. Congratulations, you now have DF.

This works fine on 64 bit machines as well.
