##### What is NextJS? Nexjs.org(The React Framework for Production) 
  - Fullstack framework for ReactJS
  - NextJS solves common problems and makes building React apps easier!

##### NextJS Key features and benefits:

1. Server-side Rendering
    - Automatic page pre-rendering Great for SEO and initial load.
    - Blending client-side and server-side: Fetch data on the server and render finishsed pages.
2. File-based Routing:
    - Define pages and routes with files and folders instead of code.
    - Less code, less work, highly understandable
3. Build Fullstack Apps:
    - Easily add backend (server-side) code to your Next /React apps
    - Storing data, getting data authentication etc. can be added to your React projects



###### Page pre-redernding

1. Static site Generation(SSG)

Generate on the build, user can view the data without any redering(useEffect)

```
export async getStaticProps(){
  return {
    props: {
      meetups: dummy_data
    },
    revalidate: 10(in sec)
  }
}
```     
2. Server side rendering (SSR)

```
export async getServerSideProps(){
  return {
    props: {
      meetups: DUMMY_DATA
    }
  }
}
```


