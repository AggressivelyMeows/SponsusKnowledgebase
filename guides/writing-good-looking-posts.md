---
description: A guide to Sponsus's Markdown flavour.
---

# Writing good looking posts

Writing posts that look good is as easy as pie with Sponsus. There are some small caveats that need to be addressed however as well as some notes on how to actually write the content. But once you finish this guide, you will be ready to rock on Sponsus!

### Types of post

Sponsus supports multiple different types of post where each one has a different layout designed to make the featured content look the best. The default type is "text" which is just the content of the post. The other types are image, video, audio, and poll.

To change the post type you can click this dropdown and select the type:

![](../.gitbook/assets/firefox_pkybko082x.png)

#### The types of post

{% tabs %}
{% tab title="Images post" %}
This are the second most popular type of post on Sponsus as it allows you to feature 1 or more images on your feed as well as still give you access to write a full length text post. When creating an image post, you will be given the option of adding images under the content segment. Here you can select some images to use in the gallery or just one to feature the single image.
{% endtab %}

{% tab title="Video post" %}
Video posts work the same as image posts however they are limited to 1 video per post. If you wish to embed more, you can use the image syntax with a Youtube or Vimeo link to create a video inside the post's content.
{% endtab %}

{% tab title="Audio post" %}
This allows you to feature an audio file with the options of selecting a cover image, background and more. This one is pretty straight forward as to what it does.
{% endtab %}

{% tab title="Poll post" %}
 You can query your audience and gather feedback using this type.
{% endtab %}
{% endtabs %}

### On the subject of images

Images on Sponsus are unique to some platforms as we have a few more features that other Markdown websites dont support. The first big note is that images look best when they are on their own line. This means seperating the image with empty lines above and below it. This means that the post will center and resize the image to look best on any device that views your wonderful post. An example of the recommended spacing:

```text
Dogs are pretty rad. Heres a dog to prove it:

![A dog pic, so adorable!](https://example.com/dog)

Some more stuff about how cool dogs are.
```

When you insert images, Sponsus will push the image to be on its own line however you can position the image as you like.

Another important factor about images on Sponsus is that you can annotate images by adding text between the square brackets. In our example above, the text "A dog pic, so adorable!" will show up below the image.

### Embeding external content on your posts

Embeds are a way to share content from others sites on Sponsus. We support almost any site however there are some that get special blocks. These special websites get extra goodies when we embed them into a post. For example, you can embed a SoundCloud song, album or profile, you can also embed the Spotify player. If you so wanted, you can embed a Google Doc or even a YouTube video. 

To embed content into your post, all you have to do is create an empty link with a url to the content you want to embed. For example: `[](https://sponsus.org/u/cerulean)`. Notice how there is not a "!" at the start and the fact that the square brackets hold no text. This tells our server to generate an embed below the paragraph the link is in. This is effectively a link but without the text. This special syntax will ask the url for its embed and place it at the end of the paragraph the empty link was in.

