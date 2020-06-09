# Writing mass messages to your sponsors

To make your life easier, Sponsus has a template engine that allows you to personalise your message without needing to write anything extra.

### How to use the template engine

The message box that you type into is what is refered as a template. We use this text that you type as a basis for what to send to the user. You can type specially coded letters and words to tell the template engine how to handle a bit of text.

For example, by typing `{{user.username}}` into the box, it will replace that bit with "Cerulean" \(or whomever you have selected\).

### Cheatsheet

You can copy paste these bits into your mass message to personalise it to your liking.

#### The insert-ables

| Code | Description |
| :--- | :--- |
| `{{user.username}}` | This is replaced by the users username. |
| `{{lifetime}}` | The amount the user has sponsored you since joining. |
| `{{tier.price}}` | The tier's price that they are sponsoring you for. |
| `{{tier.title}}` | The tier's name. |

#### Using IFs and such

You can also include extra bits for people who have given extra. By including an IF block, you can limit the text to people who pass the gate.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Code</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><code>{{if lifetime &apos;&gt;&apos; 20}}</code>
        </p>
        <p><code>Your text.</code>
        </p>
        <p><code>{{/if}}</code>
        </p>
      </td>
      <td style="text-align:left">If the user has given you more than 20,
        <br />they will be able to see the text between the blocks</td>
    </tr>
  </tbody>
</table>



