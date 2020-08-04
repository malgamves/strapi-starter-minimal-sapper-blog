# Minimal Sapper Blog Starter built with Strapi
A minimal Sapper Blog built with Strapi

This starter helps you get started building a blog with Sapper and Strapi. Feel free to fork, edit and customise it for your own use.

![Screenshot of Home Page](https://github.com/malgamves/strapi-starter-minimal-sapper-blog/blob/master/screenshot.png)

- Tutorial Status: In progress

## Features
- Minimal design 
- Page prefetching
- GraphQL first approach

## Content Model
- `Title` : Text
- `Description` : Text
- `Published` : Date
- `Body` : Rich Text
- `Slug` : Text
- `author` : Relation wth User


## In the works
- Article name in page title
- Post categories

## Pages
- A home page :`/`
- An about page :`/about`
- An articles page :`/articles`
- A single article page :`/articles/:Slug`

## Getting Started

To get started clone the repo
```bash
git clone https://github.com/malgamves/strapi-starter-minimal-sapper-blog.git
cd strapi-starter-minimal-sapper-blog
```

The project has two folders `frontend` for your Sapper frontend and `backend` for your Strapi backend.


### Frontend
The frontend is built with Sapper. This sets up your frontend.
```bash
cd frontend

npm install
```

Then run `npm run dev` to start your frontend server.

### Backend
The backend is built with Strapi. This sets up your backend.
```bash
cd backend

yarn install
```

Then run `yarn develop` to start your backend server.


## Deployment 

You can deploy your frontend by following the Sapper [deployment guide](https://sapper.svelte.dev/docs/#Deployment).

For your backend, Strapi has numerous options in it's [deployment guide](https://strapi.io/documentation/3.0.0-beta.x/getting-started/deployment.html).


## Contributing

Feel free to send over a PR for any changes you think should be included.


