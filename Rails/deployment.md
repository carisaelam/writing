# Learning how to deploy a Rails app


### Description

I am working my way through [The Odin Project](https://www.theodinproject.com) (TOP) Ruby on Rails curriculum and have reached the deployment lesson. This concept seems very opaque to me right now—I have no prior knowledge and am entering into this pretty blind. I'm documenting my first attempt at deployment to help myself in the future and to help anyone who may be in my shoes.

💡 _I'll use light bulbs to represent my "a-ha" moments._

---

> ### 💡
>
> The Rails app is **_dynamic_**, so it requires a hosting provider.

TOP describes **hosting providers** as _"server landlords"_—they own servers and rent out their digital units to us tenants. Up until this point, I have only used GitHub Pages and Netlify to host my sites. But now I need a different solution for my Rails app because it is _dynamic_.

- **Static** means that every user sees the same content. (e.g., calculator app, dictionary site, landing pages)
- **Dynamic** means that each user sees different content. (e.g., social media sites, blogs, streaming services)

My Rails app is a super simple blog CRUD situation. You can add, edit, or delete a blog post and comment on posts. This **dynamic** app requires a database and the ability to run Ruby (a server-side language).

**_Okay, so I need to pick a hosting provider._**

> ### 💡
>
> Turns out all of these --> [AWS, Azure, and Google Cloud]
> are hosting providers. I've heard people talk about these services but never understood what they were. They are all **_cloud_** providers and definitely more complex than what I need for my tiny app.

That brings us to **PaaS**
**_Platform as a Service (PaaS)_** providers are user friendly and "simple", like a landlord who covers utilities. TOP provides a list of three options for PaaS services, all of which are paid services with limited free options.

1. `Fly.io`
2. `Railway.app`
3. `Render `

I'm obviously trying _not_ to pay to host this little practice app. My focus is on getting the experience of what it means to deploy an app and how the process works. So I did some digging on the TOP Discord server and online and learned a few things.

Turns out, `Fly.io` doesn't really have a free tier anymore. Their hobby plan is not the same as it used to be, so this option is eliminated for me (and maybe also for TOP in general)

I read plenty of posts of folks mentioning how _slow_ Render is when loading up the page, and Heroku has no free plan. So Railway it is!

> ### 💡
>
> ##### Railway is my best option

### Deploying with Railway

- Went to railway.app, logged in via GitHub
- Selected `Deploy from GitHub repo` > `Deploy Now`
- It took about 2 minutes and then said "Deployment successful"...was that it?
- OOP! Approximately 10seconds later.... "CRASHED"
- So I restarted... Deployment successful "ACTIVE"... was THAT it?
- NOPE!! Crashed again. Obviously something is going wrong.

TOP gives fair warning that errors are inevitable, especially when deploying for the first time. Their advice is to remain calm and debug carefully.

I spent a full day trying to get the Railway deployment to work. I think ultimately my issue came down to me trying to change too many things without really understanding what I was doing.

> ### 💡
>
> #### RAILS_MASTER_KEY

My advice for anyone trying to do this would be to do a quick Google search and learn a bit about **RAILS_MASTER_KEY** and how that needs to work with the Railway app and your app. That should save you some heartache.

Basically, you will need to go in and generate an encrypted credentials file that should in turn create a `master.key` file. The `master.key` file will hold the key necessary to decrypt your `credentials.yml.enc` file which in turn holds a "secret_key_base" that is necessary for the success of the rest of your project. You then need to add that master key as a variable in Railway so that it has access to it during deployment. `master.key` is gitignored by default for security reasons, so Railway doesn't "see" it at all until you explicitly type it in as a variable.`

If that all sounds confusing, it's because it IS confusing, at least for someone coming at this for the first time. This [video](https://www.youtube.com/watch?v=igS0Y6hfZoM) and this [blog post](https://webcrunch.com/posts/the-complete-guide-to-ruby-on-rails-encrypted-credentials) were hugely helpful. The developer in the video uses Render to deploy, but I was still able to glean a lot of helpful information.

Finally, with a lot of help from Google/Stack Overflow/Chat GPT, I was able to get my app up and running with a Postgres database via the Railway hosting provider.

&nbsp; 

---

<div class="connect__container">
  <h4>Connect with me!</h4>

  <div class="pic__and__links__container">
    <img class="profile__pic" src="assets/profile_pic.png">
    <div class="connect__links">
      <a href="https://github.com/carisaelam">GitHub</a>
      <a href="www.linkedin.com/in/carisa-elam-097368239">LinkedIn</a>
    </div>
  </div>
</div>


<style>
.connect__container{
    display: flex; 
    flex-direction: column; 
}

.pic__and__links__container {
  display: flex; 
  gap: 2rem; 
  margin-top: 1rem; 
}

.profile__pic {
  max-width: 7rem;
  border-radius: 100%; 
}

.connect__links {
  display: flex; 
  flex-direction: column; 
  gap: .5rem; 
  justify-content: center; 
  font-weight: bold; 
}
</style>
