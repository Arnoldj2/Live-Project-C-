# Live Project C\# ASP.Net MVC

## Introduction

This was a two week live project at the tech academy where I worked other software developers to build an interactive website for a theater company to manage its website content without needing any technical knowledge.
The site included multiple areas to manage admin, subscriber, and general public needs as well as included information on the current and past productions, cast members, rental requests, and blogs.

The project was built using ASP.Net MVC and Entity Framework in C# with Bootstrap styling. We used Visual Studio as the IDE with Azure Devops and Agile/Scrum methodologies to develop this project.

This was challenging and rewarding experience being able to work with other software developers during the lifecycle of this project . I worked on several back end and front end stories all with varying degrees of difficulty. 
Below are descriptions those stories with a few code snippets.


## Back End Stories


<h3>Nav Links to Index Pages</h3>

This story required me to change the nav link into a Bootstrap dropdown using razor to make the links point to the Index pages of the models created thus far. 

```
     <li class="nav nav-item dropdown ">
        <a class="nav nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          Production
        </a>
        <div class="dropdown-menu dropdownbckgrndclr" aria-labelledby="navbarDropdownMenuLink">
          @Html.ActionLink("Cast Members", "Index", "CastMembers", new { Area = "Production" }, new { @class = "dropdown-item dropdowntxt" })
          @Html.ActionLink("Production Photos", "Index", "ProductionPhotos", new { Area = "Production" }, new { @class = "dropdown-item dropdowntxt" })
          @Html.ActionLink("Productions", "Index", "Productions", new { Area = "Production" }, new { @class = "dropdown-item dropdowntxt" })
        </div>
      </li>

```

<h3>Create an entity model for BlogPost area and CRUD pages</h3>

There were 2 parts to this story.  For the First part, I had to create a model, and then for the second part I had to create CRUD pages for it. The first part was accomplished by using a code first workflow.
I built the model first then updated the database to create a table in the database.

<h4>Model</h4>

```

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

After the model was created i used Visual Studio and EntityFramework to create the controller along with the Index, Edit, Create, Details, and Delete pages.

<h4>Controller</h4>

```

namespace TheatreCMS3.Areas.Blog.Controllers
{
    public class BlogPostController : Controller
    {
        private ApplicationDbContext db = new ApplicationDbContext();



        // GET: Blog/BlogPost
        public ActionResult Index()
        {

            return View(db.BlogPosts.ToList());
        }

        // GET: Blog/BlogPost/Details/5
        public ActionResult Details(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            BlogPost blogPost = db.BlogPosts.Find(id);
            if (blogPost == null)
            {
                return HttpNotFound();
            }
            return View(blogPost);
        }

```

<h4>Index</h4>

```

<h1 class="blogpost-h1">Index</h1>
<p class="text-center">
  @Html.ActionLink("Create New", "Create")
</p>
@foreach (var item in Model)
{

  <div class="container">
      <div class="card mt-4">
        <div class="row ">
          <div class="col-6 col-sm-12 col-md-6">
            <img class="blogpost-img-fluid" src="~/Content/images/BlogPostRobot.jpg" alt="Placeholder Image">
          </div>
          <div class=" col-6 col-sm-12 col-md-6">
            <p class="text-left font-weight-bold mt-4">@Html.DisplayFor(modelItem => item.Author)<br /><small class="text-muted">@Html.DisplayFor(modelItem => item.Posted)</small></p>
            <h4 class="text-left font-weight-bold pr-4">@Html.DisplayFor(modelItem => item.Title)</h4>
            <p class="text-left blogpost-truncatetxt blogpost-btn-spacing pr-4">@Html.DisplayFor(modelItem => item.Content)</p>
            <div class="">
              @Html.ActionLink(" Edit", "Edit", new { id = item.BlogPostId }, new { @class = "blogpost-btn-on-bottom-1 btn btn-secondary fas fa-edit" })
              @Html.ActionLink(" Details", "Details", new { id = item.BlogPostId }, new { @class = "blogpost-btn-on-bottom-2 btn btn-secondary fas fa-info-circle" })
              @Html.ActionLink(" Delete", "Delete", new { id = item.BlogPostId }, new { @class = "blogpost-btn-on-bottom-3 btn btn-danger fas fa-trash" })
            </div>
          </div>
        </div>
      </div>
    </div>

}

```

## Front End Stories

<h3> Styling Index, Edit, Create, Details, and Delete pages. </h3>

These stories involed styling the CRUD pages according provided layout and color schema. One such instance was that the index page [code shown here](#index) required that 
each BlogPost have its own container where the photo for the BlogPost is on the left and the information about the BlogPost on the right. 

![readme_img](https://user-images.githubusercontent.com/74551278/111548215-fbac6200-873f-11eb-8b40-da6c0bd46b6a.PNG)


## Final take away and other skills learned

This project was fun, engaging, and provided great real world experience. Through doing this I was able to: 
* Increase my knowledgebase of programming languages and concepts used.
* Improve the project flow by communicating with the team about roadblocks and other challenges.
* Learn new efficiencies from other developers by observing their workflow and asking questions.
* Focus on writing clean efficient code.