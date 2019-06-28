# Demonstration Application for VMware Cloud Automation Services (CAS)

This application was created to get away from demoing Wordpress as the "gold standard" of applications. Focused on creating an application that communicates between multiple tiers (3), is responsive, and leverages technologies and languages that are common place in developer communities. It was designed as cloud native first from a Docker perspective (included is the docker compose file) but also includes the Kubernetes YAML file for deploying to a Kubernetes cluster.

## Application Description 

# Tier 1 - Frontend Application - User Presentation 

* Angular 6 front end with VMware ClarityUI (https://vmware.github.io/clarity/)
* NGINX hosting Angular app and also providing reverse proxy functionality to the App Tier. Reason for this is since Angular is a client side extension, connecting to the app directly causes it to fail since it can't resolve DNS
* Guestbook/Chat/Twitter clone - post a message, it pushes to the API, and the api inserts into the database tier 
* Refreshes the inbound content via API every 2 seconds from the client browser (horribly inefficient, PR it!)
* Scalable to N number of 

# Tier 2 - App Tier - API 

* Python Flask based application
* 2 Methods, POST and GET. POST sends data to the Database, GET returns data to be visible on the screen.
* Scalable to N number of pods 
* Needs to be instantiated BEFORE the Frontend

# Tier 3 - DB Tier - Data 

* Postgresql 9.5 database (named 'posts')
* Precreated table (named 'textData') 
* Do not scale this pod; bad things will happen


## Todo's

* Add sockets.io support
* Merge flask routes into 1 route instead of 2 (RESTful Model) 
* Leverage GIT Branching to change ClarityUI theme Light to Dark
* Include new routing 
