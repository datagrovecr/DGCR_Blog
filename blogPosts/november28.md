# Organizing Resources with a Website
## Developer: Andrés Villalobos Carballo
11-21-2022


### Project Name: Guidance Site
Link to repo: https://github.com/AndresV20/Guidance-site-2 


### Project Function
The purpose of this project is to have a place where we can share resources with other developers that aren't part of the DataGrove team and with people who are looking to join the team in the near future. 


### Specific Task
My task on this project is to create the site and add the resources we've already found.

![Progress image one](https://raw.githubusercontent.com/datagrovecr/andresWork/main/homepage.png )
### Challenges
The challenges I've faced during this project have been few, nonetheless things that I'd take a long time to solve if it wasn't for the help of the team. The first one was an error when creating the react application, where first  would create it locally and dragged and dropped the file from the local repository into a repository that was being tracked by GitHub, this caused an error where the command "npm start" would return an error, the solution to this is to create the app within the GitHub repository from the get-go. The second challenge faced during the development of this project was implementing the React Router, what this does is create paths so that the you can interact with the various pages created, for example from the homepage you could access the page where we keep the resources for Dart and viceversa, the issue here was when following the documentation it was not clear what had to specified in the router paths, this caused an error in the first implemenation. In the second implementation I changed the approach and followed along a tutorial that used the React Router and added pages to the application, in a way like getting two birds with one stone, this approach helped solve this challenge. Another challenge that I faced was the first react app was created with the wrong file format, this because it created javascript files (.jsx) instead to typescript files (.tsx) this was solved with the help of the team by including the following command in the app creation process via the terminal "npx create-react-app my-app --template typescript".
![Progress image two](https://raw.githubusercontent.com/datagrovecr/andresWork/main/languagesv1.png)

### Final version of site (M.V.P)
This version of the site includes a working version of the react router, by showing a list of links that take you to the respective resource page, theres also a visual search bar, I say visual because it does not have the logic (code) that allows it to execute a search. At the bottom of the links list is where the homepage heading is.
![Final version of the site](https://raw.githubusercontent.com/datagrovecr/andresWork/main/Screenshot%202022-11-28%20at%205.55.02%20PM.png)



### Links that I found useful: 
- https://www.youtube.com/watch?v=2aumoR0-jmQ 
- https://blog.logrocket.com/creating-navbar-react/
- https://create-react-app.dev/docs/adding-typescript/

### List of tags

`typescript` `markdown` `blog` `datagrove` `vitepress` `website` `basic` `challenge` `project` `react` `reactapp` `router` `navbar`
