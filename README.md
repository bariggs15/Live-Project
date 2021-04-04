# JobPlacement

## Introduction
The final two weeks of the Tech Academy were spent as a team with fellow peers, utilizing skills learned to  develop a fully functional MVC Web Application using C#, HTML, JavaScript, CSS, etc languages. It was a great opportunity to see how Scrum-style coding works and how important it is to be responsible when working in a team setting where everyone is dependent on each other. I worked with both [back end stories](#back-end-stories) and [front end stories](#front-end-stories) with varying degrees of difficulty. It was an opportunity to work on planning and developing code, fixing bugs, and utilizing resources available to progress the project. 

Below are code snippets and descriptions of code that I worked on with full files availabe in repo. 

## Back End Stories
* [Creating a Comments Section](#Creating-a-Comments-Section)
* [Like Dislike Features](#Like-Dislike-Features)

### Creating a Comments Section
This website required a comments section in which the users could write a review of the shows/performances. Some of the features involved were required to put in a shared cshtml partial view to be used by other team members. This section allowed me to get my bearings on the project and the MVC style involved. 

  @model IEnumerable<TheatreCMS3.Areas.Blog.Models.Comment>

  @{
    ViewBag.Title = "Index";
  }

  <h2>Index</h2>

  <p>
    @Html.ActionLink("Create New", "Create")
  </p>


  @Html.Partial("_Comments")
  
        @model IEnumerable<TheatreCMS3.Areas.Blog.Models.Comment>


        @foreach (var item in Model)
        {

          var endTime = DateTime.Now;
          int numDays = Convert.ToInt32(Convert.ToDateTime(endTime).Subtract(Convert.ToDateTime(item.CommentDate)).TotalDays);

          if (item.Author == null)
          {
            <div class="comment-date "> Author , @numDays days ago </div>
          }
          else
          {
            <div class="comment-date "> @item.Author.UserName , @numDays days ago </div>
          }

          <div class="comment-message"> @item.Message</div>
          
         <div class="comment-details1">
          <a href="@Url.Action("Edit", new { id = item.CommentID })">
            <i class="comment-edit fas fa-edit"></i>
          </a>
          <a href="@Url.Action("Details", new { id = item.CommentID })">
            <i class="comment-details2 fas fa-info-circle"></i>
          </a>
          <a href="@Url.Action("Delete", new { id = item.CommentID })">
            <i class="comment-delete fas fa-trash"></i>
          </a>
        </div>



### Like/Dislike Features
Another task assigned to me was using the like/dislike button with html and Razor syntax combined with Javascript and AJAX to give a real time, updated like/dislike section of the comments.

    <div class="comments-container">
    <div class="comments-voting">
      <div class="comment-likes">
        <button id="likebtn">
          <i class="far fa-thumbs-up"></i>
        </button>
        <input type="number" id="input1" value="@item.Likes" name="" />
      </div>

      <div class="comment-dislikes">
        <button id="dislikebtn">
          <i class="far fa-thumbs-down"></i>
        </button>
        <input type="number" id="input2" value="@item.Dislikes" name="" />
      </div>

      <div class="comment-reply">  @Html.ActionLink("Reply", "Reply", new { id = item.CommentID })</div>
    </div>
    </div>

     <script type="text/javascript">
      let likebtn = document.querySelector('#likebtn');
      let dislikebtn = document.querySelector('#dislikebtn');
      let input1 = document.querySelector('#input1');
      let input2 = document.querySelector('#input2');

      likebtn.addEventListener('click', () => {
        input1.value = parseInt(input1.value) + 1;
      })
      dislikelikebtn.addEventListener('click', () => {
        input2.value = parseInt(input2.value) + 1;
      })

  </script>

*Jump to: [Front End Stories](#front-end-stories), [Back End Stories](#back-end-stories), [Page Top](#live-project)*

## Front End Stories
* [Fixed Footer for Main Page](#Fixed-Footer)
* [Formatted and Styled Comments Page](#Formatted-and-Styled-Comments-Page)

### Fixed Footer for Main Page
When I jumped in the project, one of the issues was the container for the footer was blocking much of the text on the main page. It was also not formatting properly based on screen size and layout. I utilized HTML and CSS to fix this issue.

     footer{
     margin-top:auto;
    }
    .footer-content {
        padding-top: 12px;
        padding-left: 30px;
        padding-right: 30px;
    }
    .footer-links {
        height: 24px;
        /*height has to be entered manually due to floating elements*/
        /*ensures padding/margin relative to other elements responds as expected*/
    }
    .footer-address {
        padding-top: 8px;
        line-height: 20px;
    }
    .footer-copyright {
        width: 115px;
        text-align: right;
        position: relative;
        bottom: 0;
    }
### Formatted and Styled a Comments Page
Another task assigned to me was to create a modern, "YouTube-like" comments section with appropriate styling and formatting. This also incorporated the like/dislike feature discussed above. I was able to utilize much CSS and HTML skills in this section.
      
    .comment-message {  
        justify-content: left;
        padding-top: 10px;
        background-color: black;
        color: var(--secondary-color);
        text-wrap: normal;
        font-size: larger;
    }
    .comment-date {
        border-top: 1px solid gray;
        text-align: left;
        padding-top: 10px;
        color: var(--light-color);
    }
    .comment-details1 {
        text-align: left;
        color: var(--light-color);
        padding-top: 0px;
        right:0px;
        width: 20%;
        position: absolute;
    }
    .comment-details2 {
        color: var(--light-color);
    }
    .comment-edit {
        color: var(--light-color);
    }
    .comment-delete {
        color: var(--main-color);
    }
    .comment-likes:hover{
        cursor: pointer;
    }
    .comment-dislikes:hover {
        cursor: pointer;
    }
    .comments-container{
        width: 75%;
    }
    .comments-voting {
        position: relative;
        border: 1px solid var(--dark-color);
        border-radius:1px;
        padding: 5px;
        display:flex;
        padding-top: 30px;
        width:50%;
    }
    input{
        width: 35px;
        border:none;
        background: none;
        color: var(--light-color);
        font-size: 15px;
        margin: 0 10px;
    }
    button{
        color: var(--dark-color);
        background: var(--light-color);
        font-size:15px;
        padding: 0 5px;
    }
    
