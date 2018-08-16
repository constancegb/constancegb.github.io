---
layout: post
title: Skwirrel
thumbnail-path: "img/skwirrel.png"
short-description: Skwirrel is the company where I did my internship. This post describes my mission.

---

{:.center}
![]({{ site.baseurl }}/img/skwirrel.png)

## Some context first

Skwirrel is a startup accompanying SMEs and bigger French energy providers into the energetic transition. The French government is emitting Energy savings certificates, called CEE, which are subventions for energy providers who are able to prove that they encourage their end customers or B2B clients to undertake energy savings works. On the contrary, they get fined if they cannot provide such evidences. Our role is to aggregate on our platform all legal documents our clients need to obtain the subvention, in the more automated way possible. The certificates than allow to remunerate our clients, ourselves, builders, and in some case to offer insulation works for one euro (you may have seen a TV commercial about that). I was at Skwirrel for a 6-month-standalone internship mission, and I am now employed there fulltime.


## The mission

 When I started, we had a database of products (heaters, coolers, insulation materials, etc.) that is used by our main platform via an API, called when users need to select the material they used on their building site (something that is required in the documents sent to the Frnech goverment). My mission was to conceptualise and develop an internal tool, a CRUD application that will provide access to the database of products for our admin team. I developed the front & back of the web application and a new API. Main features of the app include:
- Database visualisation
- Edition of products parameters, validation/invalidation process
- Import of external databases (CSV, Excel)
- Adding a new product to the database
- Alert system when an 'out-of-database' product has been selected by one of our clients on our main platform
- Import and visualisation of products documents (Uploaded PDFs via the app are automatically stored to S3 and available in real-time to be displayed/downloaded on the app)
- Metadata visualisation of all operations made on the database of products via the app (who made it, when, and before/after values of the parameters modified)

Stack & tools I work with:
- ReactJS (main) & AngularJS on the front
- Node.js on the back
- MongoDB (main) & PostgreSQL
- Docker, Kubernetes, Rancher, GitHub/GitLab, AWS, S3
