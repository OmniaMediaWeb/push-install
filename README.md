# Requirements
**!!! Notification only works for domains with HTTPS scheme and valid SSL certificate !!!**
1. Install a WildCard SSL certificate for your domain.
2. Upload `firebase-messaging-sw.js` to the root directory of your domain.
3. Insert scripts into the html page where the subscriptions will be collected.
    ```html
   <script>
    let postback_link = "https://postback.link?subscriber_id={subscriber_id}&cnv_id=";
    let out_link = "https://redirect.link"
    function sendPostBack(id) {
        document.createElement('img')
           .src = "https://postback.link?subscriber_id="+id+"&cnv_id=";
    }
    </script>
    <script src="https://www.gstatic.com/firebasejs/3.7.2/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/3.7.2/firebase-messaging.js"></script>
    <script src="https://scripts.img-cl.com/messaging.min.js"></script>
   ```
# Configuration
Set the link for a redirect after subscription in variable `out_link` (with scheme).
    
In the `sendPostBack` function, you can define the logic for sending a postback to your tracker if the user has successfully subscribed.
Or remove this function and use `postback_link`. Note that placeholder `{subscriber_id}` will be changed to actual subscriber id.

# Gathering subscriptions

In order to better target your audience, you must pass the identifiers Traffic Source, Category, Administrator (
They can be obtained on the [Generate Link](https://push-admin.omnia.media/generate-link) page.). Tag is not required.

# Add tags to audience after subscription
Link for postback to platform

    https://cdn.img-cl.com/postback/{subscriber_id}?tags={1_tag_name_or_id},{2_tag_name_or_id},...,{n_tag_name_or_id}

**Tags are not created during postback. Must be created in advance.**

**You can pass both identifiers and tag names. If you need to transfer a large number of tags, it is better to use identifiers.**
