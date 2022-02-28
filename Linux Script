For the Lucky Duck Investigations, there are a few tools mentioned that are used when scripting:
awk, sed, grep
We are looking for negative balances using grep. We can run the following at the command line: grep - *
If there is an issue running above, try using --: grep -- ‘-’ *
Script the above grep to create two columns of date and time:
#!/bin/bash
grep -- "-" $1_win_loss_player_data | awk -F"\t" '{print $1 }' | sed -e 's/_win_loss_player_data:/ /' > test.out
(Note: the original downloaded data files are separated by tabs. Sed is used to write only the date portion of file)
Output should look as follows:
# cat test.out 
0310 05:00:00 AM
0310 08:00:00 AM
0310 02:00:00 PM
0310 08:00:00 PM
0310 11:00:00 PM
0312 05:00:00 AM
0312 08:00:00 AM
0312 02:00:00 PM
0312 08:00:00 PM
0312 11:00:00 PM
0315 05:00:00 AM
0315 08:00:00 AM
0315 02:00:00 PM
I copy test.out file over to Dealer_Analysis to continue work:
We use the head command to see how the Dealer_schedule files look before writing the scripts.
First pass looks as follows:
# cat roulette_grep.sh 
#!/bin/bash -xvv
cat $1_Dealer_schedule | awk -F" " '{print $1 $2, $5, $6}' | grep "$2"
But, I want to read in from the test file to automate more!  My next pass looks as follows:
cat find_dealer_player_corrolation.bash 
#!/bin/bash
filename="$1"
while IFS=" " read -r date time; do
cat ${date}_Dealer_schedule| grep "$time" | awk -F" " '{print $1, $2, $5, $6}'
done < "$filename"
-----------------------------------------------
Note: Had to grep before awk otherwise the return is empty
