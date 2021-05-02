## Week 3 Homework: A High Stakes Investigation

### Scenario

You have just been hired by Lucky Duck Casino as a security analyst.

 - Lucky Duck has lost a significant amount of money on the roulette tables over the last month.

 - The largest losses occurred on March 10, 12, and 15.

 - Your manager believes there is a player working with a Lucky Duck dealer to steal money at the roulette tables.

 - The casino has a large database with data on wins and losses, player analysis, and dealer schedules.

- You are tasked with navigating, modifying, and analyzing these data files to gather evidence on the rogue player and dealer.

 - You will prepare several evidence files to assist the prosecution.

 - You must work quickly as Lucky Duck can't afford any more losses.

Lucky Duck Casino has provided you with the following files if required:

  - [Roulette Player Data: Week of March 10](https://du.bootcampcontent.com/denver-coding-bootcamp/du-den-cyber-pt-12-2020-u-c/blob/master/CourseMaterials/2-Homework/03-Terminal/Resources%20/Roulette_Player_WinLoss_0310.zip)
  - [Employee Dealer Schedule: Week of March 10](https://du.bootcampcontent.com/denver-coding-bootcamp/du-den-cyber-pt-12-2020-u-c/blob/master/CourseMaterials/2-Homework/03-Terminal/Resources%20/Dealer_Schedules_0310.zip)

**Note**: The instructions ask you to set up the files using a `wget` command, but the files are also provided in compressed zip format if the command does not work.


### Lab Environment

- You will use your local Vagrant virtual machine for today's activities. Please note that instructors and students have different access credentials.
    - Username: `sysadmin`
    - Password: `cybersecurity`

### Instructions 

Use your command-line skills to uncover the identities of the rogue casino player and dealer colluding to scam Lucky Duck out of thousands of dollars. 

After your investigation, you will provide a summary of your findings to the casino. 

#### Step 1: Investigation Preparation

Your first task is to set up directories to prepare for your investigation.

1. Begin by making a single directory titled `Lucky_Duck_Investigations`.
- `mkdir Lucky_Duck_Investigations`

2. In this directory, create a directory for this specific investigation titled `Roulette_Loss_Investigation`.
- `mkdir Roulette_Loss_Investigation`

3. In `Roulette_Loss_Investigation`, create the following directories:

    - `Player_Analysis` to investigate the casino player.
      - `mkdr Player_Analysis`
    - `Dealer_Analysis` to investigate the dealers.
      - `mkdr Dealer_Analysis`
    - `Player_Dealer_Correlation` to summarize your findings of the collusion.
      -  `mkdr Player_Dealer_Correlation`

4. Create empty files called `Notes_<Directory Name>` under each subdirectory to store investigation notes.

    - For example: `Notes_Player_Analysis`

#### Step 2: Gathering Evidence

Your next task is to move evidence from the specific days that Lucky Duck experienced heavy losses at the roulette tables.

1. Navigate to the directory where you created the `Lucky_Duck_Investigations` directory and run the following command to set up the evidence files:

   - `wget "https://tinyurl.com/3-HW-setup-evidence" && chmod +x ./3-HW-setup-evidence && ./3-HW-setup-evidence`

   After running this command your current directory should have the following subdirectories:

    - `Dealer_Schedules_0310`: Contains the dealer schedules.
    - `Lucky_Duck_Investigations`: Contains the investigation directories and notes files you created.
    - `Roulette_Player_WinLoss_0310`: Contains the data for player wins and losses.

2. The `Dealer_Schedules_0310` and `Roulette_Player_WinLoss_0310` directories contain the dealer schedules and win/loss player data from the roulette tables during the week of March 10.

     -  Since the losses occurred on March 10, 12, and 15, move the schedules for those days into the directory `Dealer_Analysis`.
     
    - Move the files for those days into the directory `Player_Analysis`.

#### Step 3: Correlating the Evidence

Your next task is to correlate the large losses from the roulette tables with the dealer schedule. This will help you determine which dealer and player are colluding to steal money from Lucky Duck.

  **Note:** Winnings for Lucky Duck Casino are indicated with a positive number and losses are indicated with a negative number.

Complete the player analysis.
  1. Navigate to the `Player_Analysis` directory.

  2. Use `grep` to isolate all of the losses that occurred on March 10, 12, and 15.

  3. Place those results in a file called `Roulette_Losses`.

  4. Preview the file `Roulette_Losses` and analyze the data.

      - Record in the `Notes_Player_Analysis` file:

        - The times the losses occurred on each day.
        - If there is a certain player that was playing during each of those times.
        - The total count of times this player was playing.
          - **Hint:** Use the `wc` command to find this value.

Complete the dealer analysis. 
  1. Navigate to the `Dealer_Analysis` directory.

  2. This file contains the dealer schedules for the various Lucky Duck casino games: Blackjack, Roulette, and Texas Hold 'Em.

      - Preview the schedule to view the format and to understand how the data is separated.

  3. Using your findings from the player analysis, create a separate script to look at each day and time that you determined losses occurred. Use `awk`, `pipes`, and `grep` to isolate out the following four fields:

      - Time
      - a.m./p.m.
      - First name of roulette dealer
      - Last name of roulette dealer

      For example, if a loss occurred on March 10 at 2 p.m., you would write one script to find the roulette dealer who was working at that specific day and time.

      - **Hint:** You will have many scripts, but only a small change is required for each script.

  5. Run all of the scripts and append those results to a file called `Dealers_working_during_losses`.

  6. Preview your file `Dealers_working_during_losses` and analyze the data.
  
      - Record in the `Notes_Dealer_Analysis` file:

        - The primary dealer working at the times where losses occurred.

        - How many times the dealer worked when major losses occurred.

3. Complete the player/employee correlation. 

   - In the notes file of the `Player_Dealer_Correlation` directory, add a summary of your findings noting the player and dealer you believe are colluding to scam Lucky Duck.

    - Make sure to document your specific reasons for this finding.

#### Step 4: Scripting Your Tasks

You manager is impressed with the work you have done so far on the investigation.  

 They tasked you with building a shell script that can easily analyze future employee schedules. They will use this to determine which employee was working at a specific time in the case of future losses.

Complete the following tasks:

1. Remain in the `Dealer_Analysis` directory.  Develop a shell script called `roulette_dealer_finder_by_time.sh` that can analyze the employee schedule to easily find the roulette dealer at a specific time.

      **Hint:** You will be using a script similar to the one you created for the dealer analysis step, but you will not output the results into a file.

    - Design the shell script to accept the following two arguments:
      - One for the date (four digits)
      - One for the time

     **Note:** The argument should be able to accept a.m. or p.m.

3. Test your script on the schedules to confirm it outputs the correct dealer at the time specified.

#### Bonus

- In case there is future fraud on the other Lucky Duck games, create a shell script called `roulette_dealer_finder_by_time_and_game.sh` that has the three following arguments:

   - Specific time
   - Specific date
   - Casino game being played

  **Hint:** The argument does not need to name the specific casino game.

### Submission Guidelines

- Move the following to the `Player_Dealer_Correlation` directory:
  - All note files
  - Evidence files:
    - `Roulette_Losses`
    - `Dealers_working_during_losses`
  - Shell script(s)

- Compress the `Player_Dealer_Correlation` folder to a zip file and submit it.


## Dealer_Loss_Correlation
#!/bin/bash

Set time/date of loss as an array
set -a time_array
time_array=$(awk '{print $1,$2}' Roulette_Losses | sed 's/ /:/1')

Combine any dealer schedule to temp file
for file in *_Dealer_schedule
do
  awk 'NR>2 { print FILENAME (NF?":":"") $0}' $file | sed \
  '$d;s/_Dealer_schedule//g;s/ //1' >> dealer_sched
done 

#### search for matches from Roulette_Losses
for time in ${time_array[@]}
do
  grep $time dealer_sched |
    awk -F"\t" '{ print $1,$3 }' |
    sed 's/:/ /1'
done | sort

#### Cleanup 
rm dealer_sched

## Dealers_working_during_Losses
- 0310:02:00:00PM	Chyna Mercado	Billy Jones	Cleveland Hanna
- 0310:08:00:00AM	Rahima Figueroa	Billy Jones	Madina Britton
- 0310:08:00:00PM	Saima Mcdermott	Billy Jones	Katey Bean
- 0310:11:00:00PM	Cleveland Hanna	Billy Jones	Rahima Figueroa
- 0312:02:00:00PM	Chyna Mercado	Billy Jones	Cleveland Hanna
- 0312:05:00:00AM	Katey Bean	Billy Jones	Evalyn Howell
- 0312:08:00:00AM	Rahima Figueroa	Billy Jones	Madina Britton
- 0312:08:00:00PM	Saima Mcdermott	Billy Jones	Katey Bean
- 0312:11:00:00PM	Cleveland Hanna	Billy Jones	Rahima Figueroa
- 0315:02:00:00PM	Chyna Mercado	Billy Jones	Cleveland Hanna
- 0315:05:00:00AM	Katey Bean	Billy Jones	Evalyn Howell
- 0315:08:00:00AM	Rahima Figueroa	Billy Jones	Madina Britton

## Notes_Dealer_Analysis
The roulette dealer working during every loss was Billy Jones.

He worked 13 times during large losses. I ran the following 
command to find this number.

#sh Dealer_Loss_Correlation.sh | wc -l

## Notes_Player_Analysis
I ran the below commands to find each time/date that a loss occured, 
and the command below that counts all players that won money on the 
3 days specified. Mylie Schmidt was playing during every loss for 
the casino. She won 13 times. 

Command to find losses:
#grep "-" *_win* | sed 's/_win_loss_player_data:/ /;s/ //2'> Roulette_Losses

#awk -F" " '{print $1,$2,$3}' Roulette_Losses | sort | { cat ; echo ;} > Notes_Player_Analysis
- 0310 02:00:00 PM
- 0310 05:00:00 AM
- 0310 08:00:00 AM
- 0310 08:00:00 PM
- 0310 11:00:00 PM
- 0312 02:00:00 PM
- 0312 05:00:00 AM
- 0312 08:00:00 AM
- 0312 08:00:00 PM
- 0312 11:00:00 PM
- 0315 02:00:00 PM
- 0315 05:00:00 AM
- 0315 08:00:00 AM

#grep -r "-" 03* | sed 's/_win_loss_player_data:/ /' | awk -F" " '{$1=$2=$3=$4=""; print $0}' | 
#### sed 's/ //g;s/,/\n/g' | sort | uniq -c | sort >> Roulette_Losses
     13 MylieSchmidt
      1 AlysiaGoodman
      1 AmirahSchneider
      1 ArjanGuzman
      1 AviGraves
      1 AydenBeil
      1 BladeRobertson
      1 BrendanLester
      1 ChanelleTapia
      1 CiaronVillanueva
      1 CoreyHuffman
      1 DerrickSchroeder
      1 ElinWormald
      1 EstherCallaghan
      1 EtienneBrady
      1 FernCleveland
      1 HakimStott
      1 HalimaLittle
      1 JadenClarkson
      1 JeromeKlein
      1 JosieDawe
      1 KaidanSheridan
      1 KerysFrazier
      1 KobeHiggins
      1 LexOakley
      1 LiliannaDevlin
      1 MaeHail
      1 McfaddenWasim
      1 MillicentBetts
      1 MontanaKirk
      1 MyaButler
      1 NolaPortillo
      1 NormanCooper
      1 RahmaBuckley
      1 RimshaGardiner
      1 ShelleyDodson
      1 SommerMann
      1 SuhaybMaguire
      1 TallulahRawlings
      1 TrixieVelasquez
      1 ValentinoSmith
      1 VladHatfield


## Notes_Player_Dealer_Coorelation

After analyzing the losses on the 3 dates listed, it is very clear that
Mylie Schmidt is the player cheating. She was playing every time the 
casino lost money. She won 13 times, while every other player who won
only won once.

After analyzing the dealer schedule and correlating that information 
with the player data and casino losses, it is very clear that Billy 
Jones is working with Mylie Schmidt to cheat. He was the only roulette
dealer working every time Mylie Schmidt won.


## roulette_dealer_finder_by_time_and_game
#!/bin/bash

date_arg=$1
time_arg=$2
##### Format: Blackjack=BJ Roulette=RL Texas Hold Em=TH
game_arg=$3

##### Combine any dealer schedule to STDOUT
for file in *_Dealer_schedule
do
  awk 'NR>2 { print FILENAME ( NF?" ":"" ) $0 }' $file | 
    # Change time format to save on typing
    # Example: "12AM"
    sed '$d;s/_Dealer_schedule//g;s/:00:00//g;s/ //2'
done |

  ##### Search for arguements
  grep -E $date_arg |
    grep -E $time_arg |

    # Search by game
    if [[ $game_arg == 'BJ' ]] ; then
      awk -F" " '{ print "Blackjack Dealer: " $3 " " $4 }'
    elif [[ $game_arg == 'RL' ]] ; then
      awk -F" " '{ print "Roulette Dealer: " $5 " " $6 }'
    elif [[ $game_arg == 'TH' ]] ; then
      awk -F" " '{ print "Texas Hold Em Dealer: "$7 " " $8 }'
    else 
      echo "Unaccepted input, accepted format:"
      echo "Blackjack=BJ"
      echo "Roulette=RL"
      echo "Texas Hold Em=TH"
    fi

## Roulette_Losses
- 0310 05:00:00AM	-$82,348	      Amirah Schneider,Nola Portillo, Mylie Schmidt,Suhayb Maguire,Millicent Betts,Avi Graves
- 0310 08:00:00AM	-$97,383	      Chanelle Tapia, Shelley Dodson , Valentino Smith, Mylie Schmidt
- 0310 02:00:00PM	-$82,348	      Jaden Clarkson, Kaidan Sheridan, Mylie Schmidt 
- 0310 08:00:00PM	-$65,348        Mylie Schmidt, Trixie Velasquez, Jerome Klein ,Rahma Buckley
- 0310 11:00:00PM	-$88,383	      Mcfadden Wasim, Norman Cooper, Mylie Schmidt 
- 0312 05:00:00AM	-$182,300	      Montana Kirk, Alysia Goodman, Halima Little, Etienne Brady, Mylie Schmidt
- 0312 08:00:00AM	-$97,383        Rimsha Gardiner,Fern Cleveland, Mylie Schmidt,Kobe Higgins	
- 0312 02:00:00PM	-$82,348        Mae Hail,  Mylie Schmidt,Ayden Beil	
- 0312 08:00:00PM	-$65,792        Tallulah Rawlings,Josie Dawe, Mylie Schmidt,Hakim Stott, Esther Callaghan, Ciaron Villanueva	
- 0312 11:00:00PM	-$88,229        Vlad Hatfield,Kerys Frazier,Mya Butler, Mylie Schmidt,Lex Oakley,Elin Wormald	
- 0315 05:00:00AM	-$82,844        Arjan Guzman,Sommer Mann, Mylie Schmidt	
- 0315 08:00:00AM	-$97,001        Lilianna Devlin,Brendan Lester, Mylie Schmidt,Blade Robertson,Derrick Schroeder	
- 0315 02:00:00PM	-$182,419       Mylie Schmidt, Corey Huffman

