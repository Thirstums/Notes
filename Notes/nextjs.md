---
title: NextJs
description: NextJs Doucmentation
sidebar_position: 2
authors: Thirsty
---
-------------

> #### Info:
>*This is my Personal documentation for Nextjs*.
>
> Links used are mostly a direct link to the Official Next.js documentation

# Main Components

## layout.js

- [Layout.js explained](https://nextjs.org/docs/app/api-reference/file-conventions/layout)

>#### a brief summary
>The **Layout.js** file is the main Entry point of the Next.js Application.
All of the **Components** are wrapped within it as its Children. Due to that if you add any code (a P tag for example) it will be displayed on every Route Page in the App.

A great way of using this feature is using a personalized Template that you want on every single Page

Another thing the Layout.js files allows is the Costumization of the HTML Document

Such as the Metadata & Language:

![Metadata](/img/layoutjsMetadata.png)

![Language](/img/layoutjsLanguage.png)

or Script tags, links and fonts.

Summerazied, if you want something across all Routes. Put it into the ***Layout.js*** File


## page.js

- [Page.js explained](https://nextjs.org/docs/app/api-reference/file-conventions/page)

>#### a brief summary
>The Purpose of the **Page.js** File is that it Represents the **Home Page Route** of the Application. it is the page you see when you go to http://localhost:3000/

## globals.css

- [Nextjs CSS explained](https://nextjs.org/docs/app/building-your-application/styling/css-modules)

>#### a brief summary
>In the **global.css file** you define the syles that apply to the **whole Application** In order for it to work, you need to have an Import in the **layout.js** file.



# Components

- [Rendering](https://nextjs.org/docs/app/building-your-application/rendering)
- [Client Components](https://nextjs.org/docs/app/building-your-application/rendering/client-components)
- [Server Components](https://nextjs.org/docs/app/building-your-application/rendering/server-components)

By Default all Components within the App folder of your Applicaitons are React Server Components

## Rendering

## Client Components

## Server Components