# Happy Diwali Terminal Animation 🎉

This script creates a festive "Happy Diwali" animation in your terminal, similar to the `cmatrix` effect.

### Prerequisites

- A Unix-based operating system (Linux or macOS)
- A terminal with basic ANSI color support

### Setup and Execution

1. **Download or Create the Script**

   Save the following script in a file named `happy_diwali.sh`:

   ```bash
   #!/bin/bash

   # Colors for festive effect
   RED='\033[0;31m'
   GREEN='\033[0;32m'
   YELLOW='\033[0;33m'
   BLUE='\033[0;34m'
   PURPLE='\033[0;35m'
   CYAN='\033[0;36m'
   WHITE='\033[0;37m'
   NC='\033[0m' # No color

   # Array of colors
   COLORS=("$RED" "$GREEN" "$YELLOW" "$BLUE" "$PURPLE" "$CYAN" "$WHITE")

   # Trap CTRL+C to exit gracefully
   trap "tput cnorm; exit" SIGINT

   # Hide cursor for effect
   tput civis

   # Clear the screen
   clear

   # Infinite loop to display the text in a "falling" style
   while true; do
       # Randomly select a color
       COLOR=${COLORS[$RANDOM % ${#COLORS[@]}]}

       # Print "Happy Diwali" at a random position on the screen
       COL=$((RANDOM % $(tput cols)))
       ROW=$((RANDOM % $(tput lines)))
       tput cup $ROW $COL
       echo -e "${COLOR}Happy Diwali!${NC}"

       # Short delay
       sleep 0.05
   done
   ```

2. **Make the Script Executable**

   Open your terminal, navigate to the directory where the script is saved, and make it executable:

   ```bash
   chmod +x happy_diwali.sh
   ```

3. **Run the Script**

   Execute the script with the following command:

   ```bash
   ./happy_diwali.sh
   ```

   You should now see "Happy Diwali" messages appearing in random colors across your terminal! 🎇

4. **Stop the Script**

   - To stop the animation, press `CTRL+C`. This will also restore your cursor visibility.
