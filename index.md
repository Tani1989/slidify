---
title       : "Disney Movies"
subtitle    : "Developing Data Products - Shiny App"
author      :  "Tanika Sharma"
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [bootstrap,interactive]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
github :
  user : Tani1989
  repo : slidify
---

## Introduction :
This presentation is a part of course in coursera Developing Data Products.
The assignment consists of two parts:

1) Create shiny application and deploy it on Rstudio's server. 
The link for the app is : https://tanika.shinyapps.io/disneyShinyapp/

2) Second, you will use Slidify or Rstudio Presenter to prepare a reproducible pitch presentation about your application.

You can find the source code at : https://github.com/Tani1989/Developing-Data-Products

### There are 3 datasets:

1. Gross_Income - information related to gross and inflation adjusted income of the movies.
2. Characters - information related to characters of the movies.
3. Directors -  infromation related to the directors of the movies.

---

## Working of Shiny App:

You can select the Dataset and the title of the movie to view the related data in the tabular form. 
<img src="./assets/img/image1.png" height="800" width="1000"/>

---

## WordCloud 
You can select the 
income i.e. Total Gross or Inflation Adjusted from the dropdown and view the wordcloud accordingly - the movie with the highest income appears to be the biggest.


## Genre
You can select the income i.e. Total Gross or Inflation Adjusted from the dropdown and view the bargraph accordingly.

---

## ui.R

       navbarPage("Disney",
                   
                   
                   tabPanel("VIEW DATA",
                            sidebarLayout(
                              sidebarPanel(
                                
                                selectInput("dataset", "Select a dataset:",
                                            choices = c("Gross Income", "Characters", "Directors")),
                                selectizeInput('columns','Select The Movie',"")),
                              
                              mainPanel(
                                
                                tableOutput("view")
                                
                              )
                            )
                            
                   ),
                   tabPanel("WORDCLOUD",
                            sidebarPanel(
                              selectInput("income1","Select Income for wordcloud",choices = c("Total Gross Income","Inflated Gross Income"))),
                            mainPanel(
                              plotOutput("cloud",width = "100%")
                            )
                            
                   ),
                   tabPanel("GENRE",
                            sidebarPanel(
                              selectInput("income","Select Income for genre",choices = c("Total Gross Income","Inflated Gross Income"))),
                            
                            mainPanel(
                              plotOutput("genre")
                            )
                            
                   )
                   
                   
)

