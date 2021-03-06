---
description: A guide to publishing content via the API
---

# Creating a post

## Logging in

Before you can do any kind of interaction with the API, you must first make sure you have a valid API key or OAuth access token with the `posts.manage_posts.write` permission. If you dont know what this means, please read our guide on authentication with the API by clicking below:

{% page-ref page="getting-logged-in.md" %}

## Creating a post programmatically

Making posts is a really simple process, all you need to do is send a few fields and we handle everything else. If you are sending any kind of data to Sponsus, it must be packaged into a JSON body. This allows us to accept data from almost every language without having to deal with compatability.

```javascript
POST https://api.sponsus.org/v1/profiles/@me
Authorization: APIKey

JSON Body:
{
    "title": "Programatic test",
    "content": "This is the content of the post! It supports **Markdown** :sparkles:",
    "price_to_view": 0,
    "type": "text",
}
```

{% hint style="info" %}
To find out what Markdown is and what you can do with it, [click here to be taken to the Writing a post guide](../guides/writing-good-looking-posts.md)!
{% endhint %}

These fields are always needed in a post request as these determine how we handle the post. Title and content are pretty obvious as to what they do however the `price_to_view` field controls how much someone would need to donate or sponsor in order to get access. The type field tells Sponsus what kind of post this is. It also helps with determining the required fields from other post types such as `images` or `video`.

If your request was successful, Sponsus will return this object:

```javascript
{
  "success": true,
  "postID": "1838293723792936960",
  "post_slug": "programatic-test12",
  "post_url": "/u/1729788214794915840/p/programatic-test12",
  "post": {
    "_id": "1838293723792936960",
    "title_slug": "programatic-test12",
    "type": "text",
    "title": "Programatic test",
    "content": "Content",
    "price_to_view": 0,
    "authorID": "1729788214794915840",
    "userID": "1729788214794915840",
    "created_at": 1581257591.59882,
    "published_at": 1581257591,
    "publish_at": null,
    "text_content": "Content",
    "preview_img": "",
    "is_nsfw": false,
    "is_hidden": false,
    "tags": [],
    "attachments": [],
    "status_message": "",
    "embeds": [],
    "fetching_embeds": false,
    "hearts_count": 0,
    "comments_count": 0,
    "views_count": 0,
    "latest_comments": [],
    "locked": false
  }
}
```

{% hint style="info" %}
The embeds field is processed after the post is created, check back after a few seconds to get the post embeds.
{% endhint %}

## Locking a post

{% hint style="danger" %}
The old method of locking posts has been deprecated for the `lock` method. Please read below as to how to use the new locking system.
{% endhint %}

Paywalling content is Sponsus's bread and butter. Its super simple to lock a post with the ability to extend it for advanced users.

When making a post \(editing or creating a new one\), you can send a "lock" object. This object tells Sponsus's API how to lock a post. This is a per-post basis to give you the most flexability.

```javascript
"lock": {
    "type": "price",
    // must be one of "disabled", "tiers", "price"
    "price": 10,
    // the minimum amount in $ a user must pay per month.
    "tiers": [
        "1811618092527259648", // an array of tierIDs you want to lock a post to
        "1738770542594494464" // this will be shown in the order you insert them.
    ],
    "allow_donations": true,
    // if the type is price then this will include donations
    // when working out if someone has enough to access the post.
    "minimum_length_of_sponsorship": 4
    // the minimum amount of months a user must sponsor in total to access
}
```

## Creating a media post \(Image gallery & Video\)

Since the first example is only a basic text post, lets go deeper into the API and create an image or video post. Most of the code used in the first example is reused here so I will only talk about the bits that have changed. The biggest thing that has changed with our media post is the fact that we are changing the type field to be either image or video.

### Creating a image post

```javascript
{
    ...
    "type": "image",
    "images": {
        "src": [
            "image1url",
            "image2url",
            "image3url"
        ]
    }
}
```

The `images.src` field must be an array as Sponsus image posts are galleries. If you only want to show off a single image, then just put one image url in the array. Image url must be **HTTPS** urls as security is strict on Sponsus. If you need to upload images that require 

### Creating a video post

```javascript
{
    ...
    "type": "video",
    "video": {
        "src": "https://www.youtube.com/watch?v=JsntlJZ9h1U"
    }
}
```

The video src field is different to the image src field as this takes a single video url as the input. The video urls that we support are YouTube, Twitch.tv \(live only\), Vimeo \(public videos for now\), and raw MP4 videos. If you try to use a url that is not supported, it will not show up on the website.

## Publishing a post at a later date

It is possible to create a post and then have it be published later on. This is called a draft as the API waits until the signal to publish the post to the sponsors. You can do this in a few ways, you can set the `publish_at` field during post creation to an **UTC** ISO datetime. You can also edit a post that is in the "draft" stage to have the publish\_at field as well. If the post is not already published, then when the time reaches the publish\_at time the API will publish it.

If you do not wish to have automattic publishing, you can opt for a programatic aproach by sending a GET request to `/v1/posts/<userID>/post/<postID>/publish`.3123123

{% hint style="info" %}
You will need to be authenticated with the API before you edit or publish a post! Both of these routes require `posts.manage_posts.write`.
{% endhint %}

