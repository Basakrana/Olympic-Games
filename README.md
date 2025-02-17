# Olympic-Games

🤾‍♀️ The "Olympic Games 2024 Insights Dashboard" aims to deliver actionable insights and a comprehensive overview of the Games. It serves as a valuable tool for sports analysts, journalists, fans, and researchers to track performance, analyze trends, and engage with the event on a deeper level. By leveraging Power BI’s robust analytics capabilities, this project ensures that users have access to the most relevant and up-to-date information at their fingertips. 🤾‍♀️

🚀 In this project i used some DAX fuctions to create measures and columns for getting valuable insights and create visualizations.🚀

### Here are all the DAX queries which i used in this project.

#### For total country.
    Country Plyaing = DISTINCTCOUNT('athletes csv'[country])

#### Total Teams.
    Playing teams = DISTINCTCOUNT('teams csv'[code])

#### Total Athletes 
    Total athletes = DISTINCTCOUNT('athletes csv'[code])

#### Total Gold medals.
    Total Gold Medals = var obj= CALCULATE(
    COUNT('medallists csv'[medal_code]),    
    'medallists csv'[medal_code] =1)
    RETURN
    IF(ISBLANK(obj),0,obj
Same Query for Silver and Bronze Medals only change medal codes.

#### Gold medal won by male athletes.
    total gold won_by_male atheles = CALCULATE([Total Gold Medals],'medallists csv'[gender]="Male")
same query for silver and bronze medals.

#### Gold medal won by female athlete.
    total gold won_by_female atheles = CALCULATE([Total Gold Medals],'medallists csv'[gender]="Female")
same query for silver and bronze medals.

#### Gold Medal wining country in particular event.
    MedalWinningCountries = 
    VAR goldMedals =
    FILTER(
        'medallists csv','medallists csv'[medal_code] = 1
    )
    RETURN
    DISTINCT(
        SELECTCOLUMNS(
            goldMedals,
            "Country",'medallists csv'[name]
        )
    )
same query for silver and bronze winning country.

#### Gold medal winning by player in particular sport.
    MedalWinningPlayers = 
    VAR Medals =
    FILTER(
        'medallists csv',
        'medallists csv'[medal_code] = 1
    )
    
    RETURN 
    SELECTCOLUMNS(
       Medals,"country",'medallists csv'[country]
    )
same query for silver and bronze medal athlete.

#### Highest medal country.
    Higest medal country = VAR MEDAL = MAX('medals_total csv'[Total])
    RETURN
    CALCULATE(VALUES('medals_total csv'[country_code]),'medals_total csv'[Total]>=MEDAL)
#### creating a column for age group. 
    age category = 
    SWITCH(
    TRUE(),
    'athletes csv'[age]>=15 && 'athletes csv'[age]<=20 ,"15-20",
    'athletes csv'[age] >20 && 'athletes csv'[age] <=25,"21-25",
    'athletes csv'[age] >25 && 'athletes csv'[age] <=30,"26-30",
    'athletes csv'[age] >30 && 'athletes csv'[age] <=35,"31-35",
    'athletes csv'[age] >35 && 'athletes csv'[age] <=40,"36-40",
    'athletes csv'[age] >40 && 'athletes csv'[age] <=45,"41-45",
    'athletes csv'[age] >45 && 'athletes csv'[age] <=50,"46-50",
    'athletes csv'[age] > 50,"50+",
    "Under 15")
#### For key highlights.
    highlights = "Total athletes "&[Total athletes]&" with "&[Total male athletes]&" male and "&[Total female athletes]&" female participants.
    The male won "&[total gold won_by_male atheles]&" gold medals and the female won "&[total gold won_by_female atheles]&" gold medals in the tournament.
    Country "&[Higest medal country]&" is the highest performing country in the tournament."
#### Gold highlight.
    gold highlights = "Total "&[Total Gold Medals]&" where Male got "&[total gold won_by_male atheles]&" Gold medals and 
    Female got "&[total gold won_by_female atheles]&" Gold medals."
Same query for Silver and Bronze medals 

# Key Insights of Paris olymmpic 2024.
206 country participate in this olympic games.

Out of 11113 Athletes their are 5658 males where 5455 are female athletes.

USA was the highest medal winning country.

Total goldmedalist are 752 where 374 are male and 378 are female athletes.

French Swimmer Leon Marchand wins maximum gold in this olympic games.


