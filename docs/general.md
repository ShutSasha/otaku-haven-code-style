# General ⚡

[Return to Table of Contents](../README.md)

## **Intro**  

Hello everyone!

At some point, we've all faced questions like: "How should I name this?", "Where should I place that?", or "How should I structure this?". This guide aims to provide clear rules and features to help keep our projects organized, safe, and well-structured.

This is a step-by-step guide designed to help you understand the basics of building and maintaining projects within our company, Otaku-Haven-team. While our focus will be on TypeScript and React, developers working with other technologies will also find valuable insights here. Let's embark on this journey to improve our coding practices together! 🚀🚀🚀



## **Naming**

### File names should be in kebab-case  ✅
> It's about **File name**
> It helps to name your files in much more clear way.  

### Examples below

```
todos-table.component.tsx
user-profile.service.ts
dashboard-header.component.tsx
login-form.styled.ts
data-fetch.util.ts
```

### Use suffixes for your file names ✅

> From time to time it's a bit hard to navigate in haystack of open files.  
> You know we have an answer for that problem - use suffixes to make file search and navigation easier.  

> Frontend:  
```
history.component.ts
calculate-outcome.container.ts
roles.util.ts
links.const.ts
manager.styled.ts
user.service.ts
post.provider.ts
history.type.ts
```  

> Backend:  
```
history.component.ts
calculate-outcome.container.ts
roles.util.ts
links.const.ts
manager.controller.ts
user.service.ts
post.entity.ts
```

> This is the list of allowed suffixes which you can use for file naming.  
> Our git hooks configured to prevent pushing files without suffixes, so be aware )  

### Use suffixes for your folder names ✅

> It's obvious but still, please, use `kebab-case` for your folders too to keep everything consistent.  

```
- modules
-- account-tracking
-- user-management
```


## **Folder structure**

### Use modular approach for large projects and medium projects ✅  

> If project which you are working on has opportunities to grow and scale it is time to think about modules.
> Modules helps you to keep your code clear and migrate easy to Micro Service architecture in future.
> We usually use the following structure:  


> Frontend:  

```
src
- services
-- service-name
--- user-auth.service.ts
--- user-stats.service.ts
--- index.ts
- modules
-- user
--- components
---- user-input.component.tsx
---- user-avatar.component.tsx
---- user-slider.component.tsx
---- index.ts
--- pages
---- user-profile.tsx
---
--- containers
---- user-page.container.ts
---- user-details-page.container.ts
---- index.ts
---
--- utils
---- crop-user-avatar.util.ts
---- index.ts
---
--- types
---- user.types.ts
---- index.ts
---
--
-
- store
- shared
- router
- assets
```


> Backend (express):  

```
src
- config
- controllers
- enums
- middlewares
- joi-schemas
- routes
- services
- templates
- types
- utils
app.ts
```

## **Tools**

### Use quality check tools ✅  

> We have an automated way to control everything that was described above - Git Hooks.  
> For our all new projects we use them, current version of hooks supports frontend, backend and smart contracts.  
