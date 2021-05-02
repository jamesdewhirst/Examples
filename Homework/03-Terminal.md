### Submission Guidelines

- Move the following to the `Player_Dealer_Correlation` directory:
  - All note files
  - Evidence files:
    - `Roulette_Losses`
    - `Dealers_working_during_losses`
  - Shell script(s)

- Compress the `Player_Dealer_Correlation` folder to a zip file and submit it.

## Note Files
#### Notes_Player_Analysis
- Name: Mylie Schmidt
- Times: 5am, 8am, 2pm, 8pm, 11pm
- Times Played: 13

#### Notes_Dealer_Analysis
- Roulette Dealers Scheduled During Losses

###### 03/10
- 12 AM Marlene Mcpherson
- 02 AM Abigale Rich
- 05 AM Billy Jones
- 08 AM Billy Jones
- 11 AM Summer-Louise Hammond
- 12 PM John-James Hayward
- 02 PM Billy Jones
- 05 PM Rahima Figueroa
- 08 PM Billy Jones
- 11 PM Billy Jones

###### 03/12
- 12 AM Marlene Mcpherson
- 02 AM Abigale Rich
- 05 AM Billy Jones
- 08 AM Billy Jones
- 11 AM Summer-Louise Hammond
- 12 PM John-James Hayward
- 02 PM Billy Jones
- 05 PM Rahima Figueroa
- 08 PM Billy Jones
- 11 PM Billy Jones

###### 03/15
- 12 AM Marlene Mcpherson
- 02 AM Abigale Rich
- 05 AM Billy Jones
- 08 AM Billy Jones
- 11 AM Summer-Louise Hammond
- 12 PM John-James Hayward
- 02 PM Billy Jones
- 05 PM Rahima Figueroa
- 08 PM Billy Jones
- 11 PM Billy Jones

#### Billy Jones = 14 shifts, he is the one...


### Notes_Player_Dealer_Analysis
##### Dealer Note for Billy Jones
###### 03/10
- 05 AM Billy Jones
- 08 AM Billy Jones
- 02 PM Billy Jones
- 08 PM Billy Jones
- 11 PM Billy Jones
###### 03/12
- 05 AM Billy Jones
- 08 AM Billy Jones
- 02 PM Billy Jones
- 08 PM Billy Jones
- 11 PM Billy Jones
###### 03/15
- 05 AM Billy Jones
- 08 AM Billy Jones
- 02 PM Billy Jones
- 08 PM Billy Jones
- 11 PM Billy Jones

##### Billy Jones: 14 shifts

#### Player Notes
- Name: Mylie Schmidt
- Times : 5AM, 8AM, 2PM, 8PM, 11 PM
- Times Played: 13

#### Summary

Mylie Schmidt was there for all 13 times when significant roullette losses happened. Billy Jones was also working those times.

## Roulette Losses
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

## Dealers Working During Losses
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

## Shell Script(s)
`grep -i '5\|8\|2\|11' *schedule | awk '{print substr($1,22,2)" "$2" "$5" "$6}'`

## Player_Dealer_Coorelation



















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



