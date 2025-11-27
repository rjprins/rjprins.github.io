# The Case of Multiple Repos

*2025-11-27*

**Your whole project should be in a single git repo!**

Really, it does! Multiple repos make teams slow and systems error prone.

 If the`frontend`, `backend`, `infrastructure`, `computation_service`, `data_pipelines`, `forecast_model` should be working together they should be in a single repo. Too often have I seen this not being case, and the effects are more costly and insidious than you'd think at first.

Let's take `frontend` and `backend`, now this might be less common these days because fullstack developers will generally not create two repositories (for reasons I will go into later). But how do you make sure your frontend and backend work correctly together if they are in separate repositories?

You will be adding another layer of version control.

Let's say a new feature is implemented in separate frontend and backend repos. How do you deploy it? You make sure the new backend is deployed before the new frontend, right? Next you'll be wanting to add tags with a release number so you remember which frontend commit relies on which backend commit.

These release tags are the second layer of version control. One that you are managing manually.

Versioned releases are great - if you are providing a library or a public API. But if this is an _application_, versions are really only useful for release notes and bug reports.  

The downsides and costs of second-layer versioning should not be underestimated. It goes further than the frustrated frontender that forgot to update the backend repository again. Crucial development processes become more complicated: 
- How do you manage deploying the different subsystems?
- How do you run the complete system locally?
- How do you test end-to-end?
- How do you do code review over a complete feature?
These issues will slow down your team; There is more to manage, you will find bugs later and will have a whole class of bugs that are not possible in a single repo.

And there are other, less obvious problems. Separate repositories create knowledge silos and ownership silos, and lower overall collaboration. They increase the friction of cross-functional work. Developers don't naturally see merge requests for other parts of a system and will be less inclined to get involved.

In a way, it is an example of Conway's Law: System architecture follows organizational structure. This is especially a risk in new teams or new companies. Developers don't know each other well yet. The team is not yet a real team. It may feel natural for each developer to start a git repository for their own subdomain.

Another reason this might happen is because developers are unsure where to put something new. They might not feel enough ownership over the project root, or don't feel  comfortable reaching out to discuss the placement of this new part.

You don't have to go full monorepo, Google-style. Instead ideally you look at what parts are connected, and put as many of those connected parts in a single repository, until you actually reach other practical limits. I'm not sure what those limits are or where they lie, but they are certainly a lot further away than commonly assumed. Hit those limits first and _then_ think about where a second layer of versioning will be worth the hassle.

These days, frontend and backend is more likely to be done by fullstack developers. They will use a single repo for both, because they won't feel this friction in collaboration. But infrastructure engineers, data scientists, and data engineers are still likely to be working in their own repositories. Or each data model may have its own repository, with its own full set of project dependencies, Makefiles, and CI/CD. Yet another tiny little project that needs managing. 

If you find yourself dealing with integration errors, or versioning to prevent integration errors: Consider merging repositories.
