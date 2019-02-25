---
id: basics
title: The basics
---

The add-ons in Stremio are the most fundamental part of the app. They provide the whole contents the users enjoy.

An add-on in Stremio, unlike other similar apps, in most cases, does not run on client's computer. It is rather hosted on the Internet, just like any website. This has ease of use and security benefits for the end user.

If add-on is served via HTTP, **CORS** headers must be present.

TODO:

The Add-on philosophy
---

 * Add-ons are not meant to compete with VOD services; they’re meant to *integrate* existing VOD services into Stremio
 * Add-ons are not meant to be used in the same way as YouTube is; You don’t upload your content to a Stremio add-on


Manifest
---

The add-on must implement the add-on API. The most important part is the **manifest**. 

The add-on manifest is JSON object describing the add-on's capabilities.

Media structure
---

Every add-on provides one or more resources for media content. The resources are organized in tree like structure. In the root of this tree we have **catalogs**. The catalogs provide media collection of different **types**. For each type we have **meta items**. These items contain **videos**. Finally for every video we have one or more **streams**. There is an option where the meta item does not contain videos. In this case it provides directly streams.

The complete tree looks like that:

    Catalog
    +-- Type
        +-- Meta Item
            +-- Videos
            +---+-- Streams

Resources
---

For Stremio to be able to display any data, it must first find it. For this purpose in every add-on's manifest, there are declared one or more resources that the add-on in question provides.

The resources are basically a segmented way to build the content tree, we talked before. Every resource is accessed at certain endpoint, where your add-on should respond with proper data.

| Resource      | Endpoint         | Description                                                                                                                                   |
| --------      | --------         | -----------                                                                                                                                   |
| **manifest**  | `/manifest.json` | The add-on description and capabilities.                                                                                                      |
| **catalogs**  | `/catalog/`      | Summarized collection of meta items. Catalogs are displayed on the Srtemio's **Board**. You can also browse the catalogs in the **Discover**. |
| **metadata**  | `/meta/`         | Detailed description of meta item. This description is displayed when the user selects an item form the catalog.                              |
| **streams**   | `/stream/`       | Tells Srtemio how to obtain the media content. It may be torrent info hash, HTTP URL e.t.c.                                                   |
| **subtitles** | `/subtitles/`    | Subtitles resource for the chosen media.                                                                                                      |

Summary
---

At this point you should be familiar with Stremio's media structure, how does add-ons work and their basic endpoints.

Fell free to proceed to the next chapter and start the guide.