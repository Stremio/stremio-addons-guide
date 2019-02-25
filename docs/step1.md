---
id: step1
title: Step 1 - The add-on manifest
---

This is the first step in our add-on guide. Here we'll create the add-on manifest for a very basic add-on.

The add-on manifest should be served on `/manifest.json` route in your add-on.

It's mandatory fields are as follow:

```json
{
    "id": "my.first.stremio.add-on",
    "version": "1.0.0",
    "name": "Hello, World",
    "description" : "My first Stremio add-on",
    "logo": "https://www.stremio.com/website/stremio-logo-small.png",
    "resources": [],
    "types": []
}
```

This is the base skeleton of Stremio's add-on manifest. In fact the `logo` field is optional, but your add-on will look much nicer and more recognizable if you use it in your advantage.

Let's look closer on our manifest.

The `id` field is arbitrary string that distinguishes your add-on among others. It's a good practice to use dot separated identifier like `com.stremio.filmon`.

The `version` must be valid [Semantic Versioning](https://semver.org/) string describing your add-on version.
`name` and `description` are descriptive fields that explain to the user what your add-on do.

The `logo` is displayed next to your add-on name and description. It should be URL to square image with resolution of 256px x 256px.

The `resources` and `types` are arrays of features that your add-on supports. We'll take a closer look at them latter on.

Install the new add-on
---

As you can see, our add-on doesn't do much right now. To see what happens create `manifest.json` with the contents above and serve it via HTTP. You can successfully install it in Stremio.

```sh
mkdir my-stremio-addon
cat > manifest.json
{
    "id": "uinique.add-on.id",
    "version": "1.0.0",
    "name": "Hello, World",
    "description" : "My first Stremio add-on",
    "logo": "https://www.stremio.com/website/stremio-logo-small.png",
    "resources": [],
    "types": []
}
^D
```

> **Note for serving Stremio add-ons**
>
> Every add-on must provide **CORS** headers for it's resources. Stremio can **not** make use of add-on that does not support CORS.

For easy serving we'll use the `http-server` node module. You can of course use your favorite HTTP server. Just do not forget to configure it to serve CORS headers.

```sh
npm -g install http-server
http-server --cors
```

By default `http-server` serves content on port 8080. It should be printed in your console window.

Your add-on should be located at `http://127.0.0.1:8080/manifest.json`

Now let's install our new add-on. Go to Stremio. Open the add-ons configuration, either by clicking on the puzzle icon in the upper right corner or you can open it from the `Settings`. Now you can copy the add-on URL from here and paste it in the field labeled `Add-on Repository URL`. You should be prompted with the installation dialog. Just press `Install` and your add-on will appear in the `My add-ons` section.

You successfully installed your first add-on. Unfortunately it is useless in it's current form so you'd better remove it by clicking on the `Uninstall` button. In the next section we'll begin adding functionality.