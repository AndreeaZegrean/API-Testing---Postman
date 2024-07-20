The scope of this project is to use all API knowledge gained throught the Software Testing course and apply them in practice, using a live application.

Application under test: **The Spotify Web API** provides a wide range of functionality for developers, including:

Retrieve data from your favorite artist, album, or show.
Search for Spotify content.
Control and interact with the playback, play and resume, seek to a position, or retrieve your queue.
Manage your personal library by creating a new playlist and adding your favorite tracks to it.
Get recommendations based on the music you listen to the most.
And much more! You can find a complete list of available endpoints in the API Reference. For more details about documentation, visit this website.

Tools used: **Postman, Newman.**

**First Steps:**
- Go to Spotify and create a new user account.
- Access the dashboard and log in with the user account you created.
- Click on the "Create an app" button.
- Enter a name and description for the new application created.
- Accept the terms and conditions and click on the create button.
- In the opened window, click on "Edit Settings."
- In the Redirect URIs textbox, enter a link. It doesn't have to be specific, but one that can be used later. Example: http://applicationcourse/callback.
- Click on the SAVE button at the bottom.

**Second Steps:**
- Open Postman aplication,you can download this Postman and create a new collection named "Spotify."
- Within the collection, create a new POST request.
- Click on authorization and select from the dropdown type OAuth 2.0.
- In the Callback URL field, enter the Redirect URIs from the first steps. If you are using the Postman web app, you don't need to set it.
- Copy the Client ID and Client Secret from your application and paste them into Postman.
- Treat these links as variables; assign them names and set them as global variables instead of using the actual links.
- In the Access Token URL field, enter the link https://accounts.spotify.com/api/token. After that, put the link https://accounts.spotify.com/authorize in the Auth URL field, and enter the text "playlist-modify-public playlist-read-private playlist-modify-private" in the Scope field.
- Finally, press "Get New Access Token". The token has been created.

The response will return an access token valid for 1 hour.

**Types available for testing**
HTTP methods supported by this API are GET, POST, PUT, PATCH, and DELETE. In this section, you can explore and perform tests on various types of operations supported by the Spotify Web API. Some examples include:

- GET Requests: Retrieve information about artists, albums, playlists, etc.
- POST Requests: Create new playlists, add tracks, etc.
- PUT and PATCH Requests: Update existing data, modify playlists, etc.
- DELETE Requests: Remove playlists, tracks, etc.

**Tests used for validation**

I send responses to some endpoints:
- https://api.spotify.com/v1/albums/1aGapZGHBovnmhwqVNI6JZ ( Get Album )
- https://api.spotify.com/v1/playlists/1qISrmv0EN157fcAD0NOaE ( Get playlist )
- https://api.spotify.com/v1/browse/categories/pop/playlists ( Get category's Playlist )
- https://api.spotify.com/v1/playlists/1qISrmv0EN157fcAD0NOaE ( Change playlyst details )
- https://api.spotify.com/v1/playlists/1qISrmv0EN157fcAD0NOaE ( Update Playlist Items )
- https://api.spotify.com/v1/playlists/1qISrmv0EN157fcAD0NOaE ( Get Playlist Items )
- https://api.spotify.com/v1/playlists/{playlist_id}/0ftNNfxBAJJeN0E7iq27fZ ( Remove Playlist Items )

**Tests performed**

_1.Get Album_
- HTTP method for request:GET.
- Get Spotify catalog information for a single album.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
![get_album_1](https://github.com/user-attachments/assets/2679839f-b7cd-4304-9a1b-799112494895)

JavaScript Tests:
![get_album_2](https://github.com/user-attachments/assets/9002f2bc-9d55-408d-86cf-ac5f57b3390a)

![get_album_3](https://github.com/user-attachments/assets/17b77b53-f421-4894-9481-a2fa806e4d3c)

_2.Get Playlist_
- HTTP method for request:GET.
- Request description:Get a playlist owned by a Spotify user.
- Response status code:201 Created.

Below you can find a picture of the API request from Postman:
![get_playlist_1](https://github.com/user-attachments/assets/ee219524-51f4-43d7-8a73-ddf9e559b568)

![get_playlist_2](https://github.com/user-attachments/assets/5b524301-1c44-471e-8e3e-e907c477b841)

JavaScript Tests:
![get_playlist_3](https://github.com/user-attachments/assets/dabe6b08-9059-4258-bd67-8abe22f65f70)

_3.GET Category's Playlists_
- HTTP method for request:GET.
- Get a list of Spotify playlists tagged with a particular category.
- Response status code:200

Below you can find a picture of the API request from Postman:
![get_category's_playlists_1](https://github.com/user-attachments/assets/95a3180f-34f4-4b7f-8336-d4ac14f0ee0c)

![get_category's_playlists_4](https://github.com/user-attachments/assets/f5e8c0ed-face-4d3a-b5d0-a15217c07a25)

JavaScript Tests:
![get_category's_playlists_2](https://github.com/user-attachments/assets/50ee576c-481d-485f-97a2-f225e2c82d49)

![get_category's_playlists_3](https://github.com/user-attachments/assets/34973f44-2faf-4158-909b-02f1a9655b3c)

_4. PUT Change Playlist Details_
- HTTP method for request:PUT.
- Request description:Change a playlist's name and public/private state. (The user must, of course, own the playlist.)
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
![put_change_playlist_details_1](https://github.com/user-attachments/assets/265f82f5-a8bf-4889-b599-b902ff1c9629)

JavaScript Tests:
![put_change_playlist_details_2](https://github.com/user-attachments/assets/32a4c340-0737-4e95-8153-ae917595657f)

_5. PUT Update Playlist Items_
- HTTP method for request:PUT.
- Either reorder or replace items in a playlist depending on the request's parameters. To reorder items, include range_start, insert_before, range_length and snapshot_id in the request's body. To replace items, include uris as either a query parameter or in the request's body. Replacing items in a playlist will overwrite its existing items. This operation can be used for replacing or clearing items in a playlist.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
![put_update_playlist_items_1](https://github.com/user-attachments/assets/f932572c-c064-4f36-9149-7972629b42d1)

JavaScript Tests:
![put_update_playlist_items_2](https://github.com/user-attachments/assets/f039ad38-0a60-455d-8419-921cab253bd8)

_6. GET Playlist Items_
- HTTP method for request:GET.
- Get full details of the items of a playlist owned by a Spotify user.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
![get_get_playlist_items_1](https://github.com/user-attachments/assets/a7619598-33ff-4c52-8868-b29d8f742cb2)

![get_get_playlist_items_2](https://github.com/user-attachments/assets/17bd6e54-3b19-4427-91f3-2a7915c0ee91)

JavaScript Tests:
![get_get_playlist_items_3](https://github.com/user-attachments/assets/57c26408-96b5-440a-bd4d-2e8049283141)

![get_get_playlist_items_4](https://github.com/user-attachments/assets/9521111d-347e-420a-b0a3-f606833a9492)

_7. DEL Remove Playlist Items_
- HTTP method for request:DEL.
- Remove one or more items from a user's playlist.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
![del_remove_playlist_items_1](https://github.com/user-attachments/assets/e0e8c71e-e081-4d82-97d8-d2b999ac4e72)

JavaScript Tests:
![del_remove_playlist_items_2](https://github.com/user-attachments/assets/355d7d52-1e8b-4674-8039-53fd4bce61f5)

**Execution report for the created API collection**

Below you can find the execution report that was generated through the Postman collection runner:
![run_1](https://github.com/user-attachments/assets/dd73876b-9aff-4b19-ba73-c7becc5ff5fc)

![run_2](https://github.com/user-attachments/assets/ac96f5dd-d880-49d7-aa4a-99a1e980a5bf)

![run_3](https://github.com/user-attachments/assets/8b7df4f6-96a6-4a5f-81e5-2d6b4b606aa0)

![run_4](https://github.com/user-attachments/assets/5edac282-faed-44b7-948d-60c12122a353)

The collection was also run through newman directly from the terminal, and the results can be found below:

![newman_collection_1](https://github.com/user-attachments/assets/517f8cf7-b199-4d18-9b6a-5846175bec0c)


