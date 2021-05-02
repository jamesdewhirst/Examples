## Here is the information I could find on my computer for this assignment. 

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
`grep -i $2 $1* | awk '{print $5" "$6}'`

## Player_Dealer_Coorelation














