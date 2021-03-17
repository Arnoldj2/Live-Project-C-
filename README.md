# Live-Project-C-
asp.net mvc

Intro 

This was a two week live project at the tech academy where I worked other software developers to build an interactive website for a theater company to manage its website content without needing any technical knowledge.
The site included multiple areas to manage admin, subscriber, and general public needs as well as included information on the current and past productions, cast members, rental requests, and blogs.

The project was built using ASP.Net MVC and Entity Framework in C# with Bootstrap styling. We used Visual Studio as the IDE with Azure Devops and Agile/Scrum methodologies to develop this project.

This was challenging and rewarding experience being able to work with other software developers during the lifecycle of this project . I worked on several back end and front end stories all with varying degrees of difficulty. 
Below are descriptions of those stories with a few code snippets.


(Reserved) Nav Link to Production Area

Change the nav link into a Bootstrap dropdown with several links for each of the Production models created so far (CastMember, ProductionPhoto).  Clicking on those links in the dropdown should take the User to that model's Index page.  Use Razor to make the links in the dropdown point to the Index pages.

Create entity model for CastMember and CRUD pages

```
using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations;
using System.Linq;
using System.Web;

namespace TheatreCMS3.Areas.Blog.Models
{
    public class BlogPost
    {

        public int BlogPostId { get; set; }
        public string Title { get; set; }
        public string Content { get; set; }
        [DataType(DataType.Date)]
        [DisplayFormat(DataFormatString = "{0:yyyy-MM-dd}", ApplyFormatInEditMode = true)]
        public DateTime Posted { get; set; }
        public string Author { get; set; }
    
    }
}

```
We need to create an entity model for the RentalSurveys class so that RentalSurveys can be saved to the database. There are 2 parts to this story. First, you will need to create a model, and then you will need to create CRUD pages for it.  
Attached is the schema for this model. After creating the model, you should update the database to create a table in the database. . You can use SQL Server Object Explorer in Visual Studio to check that the table has been created correctly. 

Production CRUD Pages Part 1: Create & Edit Styling

Rental CRUD Pages Part 3: Index Page


How was your experience working on a team of software developers?
What did you learn from working on a small piece of a larger project in the middle of its lifecycle?
What was your final take away from the Live Project? What would you do differently next time?
How can you apply what you've learned on the Live Project to your career as a software developer?