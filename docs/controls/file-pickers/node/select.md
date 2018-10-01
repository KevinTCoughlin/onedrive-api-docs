---
author: keco
ms.author: keco
ms.date: 10/01/2018
---
# Selecting Files with the Microsoft File Browser SDK

The following walkthrough demonstrates how to select files with the integrated [Microsoft File Browser SDK](https://www.npmjs.com/package/@microsoft/file-browser) and React application we covered in [Setup](index.md).

### Open demo

## 1. Pass a valid access_token to the SDK

In order to select files with the File Browser SDK, it first needs to successfully fetch items from the Microsoft Graph. Follow [this tutorial](https://developer.microsoft.com/en-us/graph/docs/concepts/auth_overview) to get a valid `access_token`. Once obtained, replace `<access_token>` with
the valid token so that it is returned as a `Promise` via `getAuthenticationToken`.

```jsx
class App extends React.Component {
  public render() {
    return (
      <GraphFileBrowser 
        getAuthenticationToken={this.getAuthenticationToken} />
    );
  }

  private getAuthenticationToken(): Promise<string> {
    return new Promise(resolve => resolve('<access_token>'));
  }
}
```

Reload your application with the above change and you should see the File Browser fetch and render items from your root drive.

The `GraphFileBrowser` component exposes the following callback props, `onSuccess` and `onCancel`. The `onSuccess` callback is invoked when a User
selects (a) file(s) via the default "Select" action button. The `onCancel` callback is invoked when a User cancels a select action via the default "Cancel" action button.

### Select File Callback

The `onSuccess` prop expects a function that receives an Array of keys for the items selected in the File Browser. An example usage of the prop is:

```jsx
class App extends React.Component {
  public render() {
    return (
      <GraphFileBrowser 
        getAuthenticationToken={this.getAuthenticationToken}
        onSuccess={this.onSuccess} />
    );
  }

  private getAuthenticationToken() {
    return new Promise(resolve => resolve('<access_token>'));
  }

  private onSuccess(keys) {
    console.log('onSuccess', keys);
  }
}
```

With the above code, one can select (a) file(s) in the File Explorer. Upon clicking the default "Select" action button, the selected keys will be output to the Browser's console.

### Cancel Callback

The `onCancel` prop expects a function which receives an `Error` as its only argument upon selection of the default "Cancel" action button. Building upon our previous example, an example usage of the prop is:

```jsx
class App extends React.Component {
  public render() {
    return (
      <GraphFileBrowser 
        getAuthenticationToken={this.getAuthenticationToken}
        onSuccess={this.onSuccess} />
    );
  }

  private getAuthenticationToken() {
    return new Promise(resolve => resolve('<access_token>'));
  }

  private onSuccess(keys) {
    console.log('onSuccess', keys);
  }

  private onCancel(err: Error): void {
    console.log('onCancel', err.message);
  }
}
```

With the above code, one can click the default "Cancel" action button. Upon doing so an `Error` with the canceled by User message will be output to the Browser's console.

### Using the onSuccess response objects

!!TODO!!

### Next Steps

* [Additional File Browser Props](additional-props.md)
* [Customizing the File Browser SDK](customization.md)

<!-- {
  "type": "#page.annotation",
  "description": "Use the JavaScript picker and saver SDKs to connect your web app to OneDrive.",
  "keywords": "js,javascript,onedrive,picker,saver,open,save,cloud",
  "section": "sdks",
  "headerAdditions": [
    "<script type=\"text/javascript\" src=\"https://js.live.net/v7.0/OneDrive.js\"></script>"
  ],
  "footerAdditions": [
    "<link rel=\"stylesheet\" type=\"text/css\" href=\"js-sample.css\" />",
    "<script type=\"text/javascript\" src=\"unified-js-sample.js\"></script>"]
} -->
