# Financial-Investment-Tool
[![Frontend CI](https://github.com/ParasX1/Financial-Investment-Tool/actions/workflows/node.js.yml/badge.svg)](https://github.com/ParasX1/Financial-Investment-Tool/actions/workflows/node.js.yml)
[![Backend CI](https://github.com/ParasX1/Financial-Investment-Tool/actions/workflows/python-app.yml/badge.svg)](https://github.com/ParasX1/Financial-Investment-Tool/actions/workflows/python-app.yml)

# Hello fellow techlauncher student
This is not the main assignment fork, this is my own test fork that I'm using to try stuff out 
with other technologies, I'm not in your group. pls ignore, and good luck!

---

The Financial Investment Tool is a web-based platform for investors and portfolio managers. It allows users to analyze stock data, calculate performance metrics, and optimize portfolios. Key features include performance metrics, correlation analysis, and machine learning for predictive analytics, all with an intuitive interface.

## Getting Started
FIT. is entirely containerised, you can hack away at it directly off of a locally run k8s cluster. Tilt is used to automatically rebuild
containers when their dependent files have changed. 

Install the following to get started
- Docker
- Some k8s dev solution - minikube works fine
- [tilt](https://tilt.dev/)

Then simply run the tilt stack and wait for everything to install and start up. 

```
tilt up
```
Any changes you make to the client and server `src/` folders should automatically hot-reload the pods.

The k8s cluster running on your machine should include the entire FIT. stack.

## Testing

### Mocking the supabase instance
The supabase instance needs to be run locally to run the API tests. This prevents us from 
going over our usage limits for basically no reason.

Install the supabase CLI [as per the docs.](https://supabase.com/docs/guides/cli/getting-started?queryGroups=platform&platform=linux). 

Install [Docker Desktop](https://docs.docker.com/desktop/)

From the project root run

```
supabase start
```
On first run, this installs all the dependencies (which takes some time).

Pull from the remote database with 

```
superbase db pull
```

The database password is in the discord.

### Testing the backend API
The tests rely on the local superbase database, currently there is no automated way of inserting test data into the
database. This needs to be done by hand.

Additionally, there is no configuration for running the local database on the CI, tests come with the boolean `RUNNING_CI`
to determine whether to skip tests that rely on the local database. At this stage, it is more effort than its worth to
run the supabase instance as a task and we will opt for local testing instead.
