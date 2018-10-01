---
author: keco
ms.author: keco
ms.date: 10/01/2018
ms.topic: overview
---
# Microsoft File Browser SDK for Node.js (Preview)

The Microsoft File Browser SDK for Web apps is the fastest way to integrate OneDrive
into your website. Open and save files to OneDrive by using a button, or
just a few lines of JavaScript - all without handling authentication. The
OneDrive picker and saver SDK for Web apps is different from other
OneDrive picker and saver SDKs because you can start using it without
downloading anything.

In this guide, we’ll show you how to get your React app quickly
[fetching files](#opening-files-from-onedrive) from the [Microsoft Graph](https://developer.microsoft.com/en-us/graph).

## Setting up

You will need to provide a valid `access_token` via `getAuthenticationToken` so that
the SDK can fetch and act upon files from the Microsoft Graph.
[This tutorial](https://developer.microsoft.com/en-us/graph/docs/concepts/auth_overview) outlines
the steps to do so.

Then, to start rendering the file library, include the script in your web app. If you are using
a CDN:

```html
<script type="text/javascript" src="//unpkg.com/@microsoft/file-browser"><script/>
```

If you are using [NPM](https://www.npmjs.com/):

```shell
$ npm i --save @microsoft/file-browser
```

Currently, the SDK relies on several peer dependencies. The bundle requires its consumers to provide `react` and `react-dom`.
If you are using TypeScript, the package also relies on typings for React and `office-ui-fabric-react`. The `office-ui-fabric-react` components
themselves are included in the bundle.

Here is an example `package.json` excerpt showing the dependency on `@microsoft/file-browser` with appropriate peer dependencies:

```json
"dependencies": {
  "@microsoft/file-browser": "~1.0.0-preview.0",
  "office-ui-fabric-react": "^5.123.0",
  "react": "^16.5.2",
  "react-dom": "^16.5.2",
},
"devDependencies": {
  "@types/react": "^16.4.14",
  "@types/react-dom": "^16.0.7"
}
```

### Next Step

* [Selecting files with the File Browser SDK](select.md)
* [Customizing the File Browser SDK](customization.md)

## Supported browsers

The `@microsoft/file-browser` supports the following browsers:

* Latest version of Edge
* Latest version of Chrome
* Latest version of Firefox
* Latest version of Safari
* Internet Explorer 9+

<!-- {
  "type": "#page.annotation",
  "description": "Use the JavaScript File Browser SDK to connect your web app to the Microsoft Graph.",
  "keywords": "js,javascript,onedrive,graph,file,browser,picker,saver,open,save,cloud",
  "section": "sdks",
  "headerAdditions": [
  ],
  "footerAdditions": [
  ]
} -->
