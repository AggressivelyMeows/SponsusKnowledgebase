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
    "content": "Content",
    "price_to_view": 0,
    "type": "text",
}
```

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

The `images.src` field must be an array as Sponsus image posts are galleries. If you only want to show off a single image, then just put one image url in the array.

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

The video src field is different to the image src field as this takes a single video url as the input.

