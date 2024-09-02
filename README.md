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

#### Highest medal country.
    Higest medal country = VAR MEDAL = MAX('medals_total csv'[Total])
    RETURN
    CALCULATE(VALUES('medals_total csv'[country_code]),'medals_total csv'[Total]>=MEDAL)
#### For key highlights.
    highlights = "Total athletes "&[Total athletes]&" with "&[Total male athletes]&" male and "&[Total female athletes]&" female participants. The male won "&[total gold won_by_male atheles]&" gold medals and the female won "&[total gold won_by_female atheles]&" gold medals in the tournament. Country "&[Higest medal country]&" is the highest performing country in the tournament."
#### Gold highlight.
    gold highlights = "Total "&[Total Gold Medals]&" where Male got "&[total gold won_by_male atheles]&" Gold medals and Female got "&[total gold won_by_female atheles]&" Gold medals."

## 🚀 Exciting Project Alert! 🚀

I'm thrilled to share my latest project, where I dove deep into the Food & Beverage Market to uncover valuable insights using Power BI. 📊

🌟 Project Highlights:

💠 Analyzed a survey of 10,000 respondents across 10 Indian cities for CodeX, a leading German beverage company entering the Indian market.

💠 Visualized data to reveal key trends and preferences in the industry, aiding CodeX in making data-driven decisions for their product launch.

This project was a fantastic opportunity to apply my data analysis and visualization skills to a real-world challenge, helping a global brand succeed in a new market🌍

🔗 Curious to learn more? Check out the full project here: https://lnkd.in/db6pCv2N

I'm always eager to improve my skills, so if you have any suggestions or feedback, I'd love to hear from you!💡

hashtag#DataScience hashtag#PowerBI hashtag#MarketInsights hashtag#DataAnalysis hashtag#FoodAndBeverage hashtag#DataVisualization hashtag#CodeX hashtag#LearningAndGrowth
