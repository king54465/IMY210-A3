# Reflection – IMY210 Assignment 3

## GitHub Repository
https://github.com/king54465/IMY210-A3

## Commands to Run the Project

### Run Strapi backend:
cd backend
docker build -t strapi-blog .
docker run -p 1337:1337 strapi-blog

### Run Nuxt frontend:
cd frontend
docker build -t nuxt-blog .
docker run -p 3000:3000 nuxt-blog

## Reflection

This assignment was a valuable but challenging learning experience. 
Going into it, I had little to no knowledge of Docker or Strapi, so 
everything felt overwhelming at first. Learning to navigate new tools 
meant I had to familiarise myself with unfamiliar icons, buttons, and 
interfaces before I could even begin building.

One of the biggest challenges was understanding Docker. I had never 
used it before and did not realise how powerful it was. Learning that 
Docker could be used to containerise and run full applications like a 
Strapi backend and a NuxtJS frontend was eye-opening. Setting up the 
Dockerfiles and understanding how each one worked took time, but once 
it clicked, it made sense why developers rely on it so heavily.

Strapi was another new tool for me. I had never built or managed a 
headless CMS before, and learning how to create content types, manage 
blog posts, and expose API endpoints was a completely new experience. 
Being able to build a functioning blog with real data coming from an 
API felt like a big achievement.

Overall this assignment pushed me out of my comfort zone and taught 
me practical skills I had never encountered before. I now have a much 
better understanding of how modern web applications are structured and 
deployed, and I feel more confident working with new technologies in 
the future.