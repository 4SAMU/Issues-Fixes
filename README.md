# Issues and Fixes

# .gitignore

## unable to ignore files even after adding into **`.gitigore`** file

There could be several reasons why your `.gitignore` file is not ignoring certain files.
Here are a few possibilities:
-The files were already added to your repository before you added them to your `.gitignore` file. Adding files to `.gitignore` does not remove them from the repository. To remove them, you need to run git rm --cached <file> for each file.
-You may have specified the wrong path or filename in your `.gitignore` file. Double-check that the paths and filenames are correct, and that they match the files you want to ignore.
-Git may be ignoring your `.gitignore `file. Check that your `.gitignore` file is in the root of your repository and that its filename is spelled correctly. If Git is still ignoring your `.gitignore` file, you can force it to read the file by running git add -f `.gitignore`.
-The files you want to ignore may already be tracked by Git. In this case, you need to remove them from the repository and commit the changes. You can do this with the following commands:

```shell
git rm -r --cached .
git add .
git commit -m "Removed files from repository"

```

# Babel compiling & npm publishing

## JS

**`example you have this folder u want to compile:`**

```shell
MyModal
├── src
│   └── Modal.js
├── package.json
└── ...
```

First install with the command below

```shell
npm i @babel/cli @babel/core @babel/preset-env @babel/preset-react
```

### In the `package.json` add the following

```json
"devDependencies": {
    "@babel/cli": "^7.21.5",
    "@babel/core": "^7.21.8",
    "@babel/preset-env": "^7.21.5",
    "@babel/preset-react": "^7.18.6",
  },
"scripts": {
"build": "babel src --out-dir lib"
},
"babel": {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react",
      "@babel/preset-typescript"
    ]
  },

```

## TS

**`example you have this folder u want to compile:`**

```shell
MyModal
├── src
│   └── Modal.tsx
├── package.json
└── ...
```

First install with the command below

```shell
npm i @babel/cli @babel/core @babel/preset-env @babel/preset-react @babel/preset-typescript
```

### In the `package.json` add the following

```json
"devDependencies": {
    "@babel/cli": "^7.21.5",
    "@babel/core": "^7.21.8",
    "@babel/preset-env": "^7.21.5",
    "@babel/preset-react": "^7.18.6",
    "@babel/preset-typescript": "^7.21.5"
  },
"scripts": {
"build": "babel src --out-dir lib --extensions .ts,.tsx"
},
"babel": {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react",
      "@babel/preset-typescript"
    ]
  },

```

## After compiling run:

```shell
npm run build  #u will get a lib folder with all the compiled files
```

## Then to publish your package:

```shell
npm login #first authenticate yourself in the npm registry then:
npm publish
```

## Reloading Vscode

in vscode:

- `Ctrl+Shift+P`
- type `Reload`
- click `Developer: Reload Window`

## Media Queries Breakpoints

### By default, Material-UI follows a predefined set of breakpoints with the following pixel values:

- xs: Extra small screens (0px and up)
- sm: Small screens (600px and up)
- md: Medium screens (960px and up)
  -lg: Large screens (1280px and up)
- xl: Extra large screens (1920px and up)

## How to use Typeform in Next.js

```js
import React, { useEffect } from "react";
import { PopupButton } from "@typeform/embed-react";
import { CenterItems, HireUs } from "@/styles/PortfolioStyles";

const Typeform = (props: any) => {
  const { IsGetStarted } = props;
  useEffect(() => {
    const script = document.createElement("script");
    script.src = "//embed.typeform.com/next/embed.js";
    script.async = true;
    document.body.appendChild(script);
    return () => {
      document.body.removeChild(script);
    };
  }, []);

  return (
    <PopupButton
      id=" " // typeform id
      style={{
        position: "relative",
        background: "none",
        border: "none",
        top: IsGetStarted ? "21px" : "44px",
        ...(!IsGetStarted && {
          ...CenterItems,
        }),
      }}
    >
      <HireUs
        variant="contained"
        sx={{
          ...(IsGetStarted && {
            borderRadius: "0 !important",
            width: " 204px",
            left: "0",
            transform: "none",
          }),
        }}
      >
        Hire Us!
      </HireUs>
    </PopupButton>
  );
};

export default Typeform;
```

## Countries flag by code

`e.g`, KENYA's code is KE

```js
const option={
code:"KE"
}
const KenyanFlag=https://flagcdn.com/w20/${option.code.toLowerCase()}.png
<img src='KenyanFlag' alt="KE"/>
```

`Output`
<img src="https://flagcdn.com/w20/ke.png" alt="KE"/>




# High Order Component Layout for Next.js

### Create a folder called components and add the following files

### `Navbar.tsx`

```ts
//LandingLayout.tsx
import React from "react";
import Navbar from "./Navbar";
import Footer from "./Footer";

const LandingLayout = ({ children }) => {
  return (
    <Navbar/>
      <main>{children}</main>
    <Footer/>
  );
};
```

### `DashboardNavbarLayout.tsx`

```ts
//DashboardNavbarLayout.tsx
import React from "react";
import TopBar from "./TopBar";
import SideBar from "./SideBar";

const DashboardNavbarLayout = ({ children }) => {
  return (
    <>
      <TopBar />
      <SideBar />
      {children}
    </>
  );
};
```

### `withLayout.tsx` the HOC Layout

```ts
// components/withLayout.js
import React from "react";
import LandingLayout from "./LandingLayout";
import DashboardNavbarLayout from "./DashboardNavbarLayout";

const withLayout = (PageComponent, layoutType) => {
  switch (layoutType) {
    case "landing":
      return (props) => (
        <LandingLayout>
          <PageComponent {...props} />
        </LandingLayout>
      );
    case "dashboard":
      return (props) => (
        <DashboardNavbarLayout>
          <PageComponent {...props} />
        </DashboardNavbarLayout>
      );
    default:
      return PageComponent;
  }
};

export default withLayout;
```

### usage example

Now, you can use the `withLayout` HOC to wrap your pages with the appropriate layout:

```ts
// pages/index.js
import React from "react";
import withLayout from "../components/withLayout";

const HomePage = () => (
  <>
    <h1>Welcome to the Home Page</h1>
    <p>This is the content of the home page.</p>
  </>
);

export default withLayout(HomePage, "landing");
```

```ts
// pages/dashboard.js
import React from "react";
import withLayout from "../components/withLayout";

const DashboardPage = () => (
  <>
    <h1>User Dashboard</h1>
    <p>This is the user dashboard content.</p>
  </>
);

export default withLayout(DashboardPage, "dashboard");
```
