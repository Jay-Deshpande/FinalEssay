# Cambridge Bitcoin Electricity Consumption Index

![Image of Main Page](/main.png)

*Image 1*

## Introduction

https://cbeci.org is an online dashboard that visualizes the total bitcoin network power. It is hosted by the University of Cambridge Judge Business School's Centre for Alternative Finance. It is difficult to accurately calculate the electricity consumption of the bitcoin network, so the Cambridge Bitcoin Electricity Consumption Index computes a 'best-guess' estimate based on calculated lower and upper bounds. The organization attempts to provide a constantly-updating, standardized metric that helps viewers understand the bitcoin network's electricity use. This is important because it is difficult to find high quality data sources for this kind of information. 

![Image of chart](/chart.png)

*Image 2*

The website consists of the main estimates (Image 1). It also has a chart tracking the metric over time (Image 2). Additionally, they provide the methodology and processes for calculating the index (Image 3). A map of mining power use by country is also provided (Image 4). Finally, In researching the website I found the javascript code that provides responses in json (Image 5).

![Image of methodology](/methods.png)

*Image 3*

![Image of map](/map.png)

*Image 4*

As shown in Image 4, the dashboard includes a web map component to visualize mining electricity use around the world. It is extremely bare bones, without a legend, north indicator, scale indicator, etc.; but it is a simple map of the world that does not attempt to provide any detailed geographic data. Therefore, only the absent legend is detrimental to the understanding provided by the map. The proportional symbols alone do not convey enough information to construct a satisfying visualization. Correspoding values in a legend would help further my understanding of the topic. 

Bitcoin is ever-more ubiqutous in the common lexicon and people are searching for information at ever-increasing rates. Much of this is spurred by hype regarding the price, but people are learing more about the underlying technology as well. The Cambridge Bitcoin Electricity Consumption Index is an important resource for people who want to discover more about bitcoin's energy use and contribution to global CO2 emissions. One of the main criticisms of bitcoin is the amount of electricity used to support the network. This dashboard is the best guess for current energy usage, and can help individuals and organizations shape their opinions of bitcoin's efficacy.

All of the dynamic data used in the model parameters comes from https://coinmetrics.io. 

Many people contributed to the Cambridge Bitcoin Electricity Consumption Index, so I will provide the official contributer information. The following is an excerpt from the CBECI's author recognition page:

>The CBECI is an ongoing project created and maintained by the Cryptocurrency and Blockchain Programme Team (Michel Rauchs, Apolline Blandin, Anton Dek, and Yue Wu) at the Cambridge Centre for Alternative Finance, University of Cambridge, Judge Business School. Special thanks go to Kyrylo Manakhov for designing the website and to Marc Bevand, Lena Klaaßen, and Christian Stoll for reviewing the methodology. The research team would also like to thank Keith Bear, Kieran Garvey, Grigory McKain, Stephen McKeon, Robert Wardrop, and Bryan Zhang for providing valuable feedback and suggestions. Furthermore, we would like to express our gratitude to Alexi Anani, and Hatim Hussain for their contributions to this project.


## Analysis of System Architecture

After some digging around the website, it appears as though the data from coinmetrics.io is gathered by the back end and served as json to the front end. They are likely making api calls or using websockets to get data, and then the calculations are made in real time in the front end. 

![Image of response json](/response.png) 

*Image 5*

Here is an image showing the responses that are generated every 30 seconds by the updating data. This is how they update the site every 30 seconds. They use the data to construct a lower bound of electricity use, and upper bound of electricity use, and a 'best-guess' that uses the most up to date. 

They also use assumed parameters in the calculations, like the price of electricity. When electricity prices are low, more people will mine bitcoin because of the lower cost. The inverse is true when electricity prices are high. The website enables the user to adjust parameters like the cost of electricity so they can see how electricity use reacts in the model. This is an interaction between the front end and back end and is a part of dynamic programming. It is a feature that makes the service more interesting and interactive.

The latest calculations are then stored in a database in the back end and are used to serve historical data to the various time series charts and mining map.

## UI/UX Design Critique

The design for the main dashboard is simple and easy to read but it lacks meaningful context. I assume this is intentional on the creator's part; they want the viewer to draw their own conclusions from the data. I understand this, but still think it would be helpful if they provided a comparison to common energy use cases. I can't really conceptualize 151.75 TWh of annualised consumption so it would be helpful for them to mention that Sweden, for example, has around 130 TWh of annualised electricity consumption.

I do like that I can change the price of electricity assumed in the model and view the effects instantly on screen. It helps to make the program more responsive. I also like that the data is updated every 30 seconds because it lets me know that I am getting the latest updates and am not relying on some article written months ago.

The least effective part of the website is the bitcoin mining map (Image 4). For one, when you click on a symbol it is highlighted, but then no additional data is shown. The symbols are also very similar in size and are very difficult to compare. The time scale bar is also unintuitive and inflexible: I can only select one time period. It is nice that they included a more detailed China map for individual provinces but I would like to see this data for other countries as well. The good part about the map is that it is very simple, so it loads and renders fast. The baselayer is gray and contains bare minimum labeling. The thematic layer is simply the proportional symbol for each country's monthly hashrate.

# Broader Connections

The Cambridge Bitcoin Electricity Consumption Index is a service that sits at the crossroads of numerous topics that we discussed this quarter. This is partly because bitcoin itself sits at these crossroads. We can use geography to help explain certain aspects of bitcoin and the effect it has on society. Since the website is basically a dashboard with a webmap, it is helpful in synthesizing the potential uses of the topics we worked on in class. One area that could be improved, is the interactivity of the visualizations. One thing that we discussed in class was how to create a more immersive and intuitive visualization. The authors of the website especially failed the mark with a boring web map that is barely interactive.

The Cambridge Bitcoin Electricity Consumption Index mining map helps us see that hundreds of thousands of people across the world are consuming electricity in support of the bitcoin network. We can use this output to calculate carbon emmissions and start to see the true contribution of digital currencies to pollution. I mentioned earlier that one of the main criticisms of bitcoin is that it uses the same amount of electricity annually as many mid-size countries. We are basically trading carbon emissions for virtual gold. This is a fact that we are going to have to grapple with: is the environmental impact of cryptocurrencies worth it?

Digital currencies seem to become more and more useable and accepted as time passes. This could widen the digital divide, between those with ready access and exerpience with the digital world and those without. They can also help disrupt traditional power structures like governments and central banks. Certain cryptocurrencies are also private and virtually untraceable, which further protects the privacy of individuals making transactions. I think that digital currencies with privacy built in will become very important in a future where one's every move and purchase is collected in data and scrutinized by governments and companies. They help provide a barrier to some of the excessive surveillance that we encounter today, and are likely to increasingly encounter in the future. Overall, I expect that digital currencies will help level the playing field for people all across the world. We now, for the first time ever, can have a completely decentralized form of currency that works across the entire world. People no longer are subject entirely to the whims and rules of a central bank manipulating currencies, for better or worse!
