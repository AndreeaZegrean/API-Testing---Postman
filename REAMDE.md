The scope of this project is to use all API knowledge gained throught the Software Testing course and apply them in practice, using a live application.

Application under test: The Spotify Web API provides a wide range of functionality for developers, including:

Retrieve data from your favorite artist, album, or show.
Search for Spotify content.
Control and interact with the playback, play and resume, seek to a position, or retrieve your queue.
Manage your personal library by creating a new playlist and adding your favorite tracks to it.
Get recommendations based on the music you listen to the most.
And much more! You can find a complete list of available endpoints in the API Reference. For more details about documentation, visit this website.

Tools used: Postman, Newman.

Link to collection : ......

First Steps:
- Go to Spotify and create a new user account.
- Access the dashboard and log in with the user account you created.
- Click on the "Create an app" button.
- Enter a name and description for the new application created.
- Accept the terms and conditions and click on the create button.
- In the opened window, click on "Edit Settings."
- In the Redirect URIs textbox, enter a link. It doesn't have to be specific, but one that can be used later. Example: http://applicationcourse/callback.
- Click on the SAVE button at the bottom.

Second Steps:
- Open Postman aplication,you can download this Postman and create a new collection named "Spotify."
- Within the collection, create a new POST request.
- Click on authorization and select from the dropdown type OAuth 2.0.
- In the Callback URL field, enter the Redirect URIs from the first steps. If you are using the Postman web app, you don't need to set it.
- Copy the Client ID and Client Secret from your application and paste them into Postman.
- Treat these links as variables; assign them names and set them as global variables instead of using the actual links.
- In the Access Token URL field, enter the link https://accounts.spotify.com/api/token. After that, put the link https://accounts.spotify.com/authorize in the Auth URL field, and enter the text "playlist-modify-public playlist-read-private playlist-modify-private" in the Scope field.
- Finally, press "Get New Access Token". The token has been created.

The response will return an access token valid for 1 hour.

Types available for testing
HTTP methods supported by this API are GET, POST, PUT, PATCH, and DELETE. In this section, you can explore and perform tests on various types of operations supported by the Spotify Web API. Some examples include:

- GET Requests: Retrieve information about artists, albums, playlists, etc.
- POST Requests: Create new playlists, add tracks, etc.
- PUT and PATCH Requests: Update existing data, modify playlists, etc.
- DELETE Requests: Remove playlists, tracks, etc.

Tests used for validation

I send responses to some endpoints:
- https://api.spotify.com/v1/albums/1aGapZGHBovnmhwqVNI6JZ ( Get Album )
- https://api.spotify.com/v1/playlists/1qISrmv0EN157fcAD0NOaE ( Get playlist )
- https://api.spotify.com/v1/browse/categories/pop/playlists ( Get category's Playlist )
- https://api.spotify.com/v1/playlists/1qISrmv0EN157fcAD0NOaE ( Change playlyst details )
- https://api.spotify.com/v1/playlists/1qISrmv0EN157fcAD0NOaE ( Update Playlist Items )
- https://api.spotify.com/v1/playlists/1qISrmv0EN157fcAD0NOaE ( Get Playlist Items )
- https://api.spotify.com/v1/playlists/{playlist_id}/0ftNNfxBAJJeN0E7iq27fZ ( Remove Playlist Items )

Tests performed

1.Get Album
- HTTP method for request:GET.
- Get Spotify catalog information for a single album.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
poza get_album_1

JavaScript Tests:
poza get_album_2

poza get_album_3

2.Get Playlist

- HTTP method for request:GET.
- Request description:Get a playlist owned by a Spotify user.
- Response status code:201 Created.

Below you can find a picture of the API request from Postman:

poza get_playlist_1
poza get_playlist_2

JavaScript Tests:
poza get_playlist_3

3.GET Category's Playlists
- HTTP method for request:GET.
- Get a list of Spotify playlists tagged with a particular category.
- Response status code:200

Below you can find a picture of the API request from Postman:
get_category's_playlists_1
get_category's_playlists_4

JavaScript Tests:
poza get_category's_playlists_2
poza get_category's_playlists_3

4. PUT Change Playlist Details
- HTTP method for request:PUT.
- Request description:Change a playlist's name and public/private state. (The user must, of course, own the playlist.)
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
put_change_playlist_details_1

JavaScript Tests:
put_change_playlist_details_2

5. PUT Update Playlist Items
- HTTP method for request:PUT.
- Either reorder or replace items in a playlist depending on the request's parameters. To reorder items, include range_start, insert_before, range_length and snapshot_id in the request's body. To replace items, include uris as either a query parameter or in the request's body. Replacing items in a playlist will overwrite its existing items. This operation can be used for replacing or clearing items in a playlist.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
put_update_playlist_items_1

JavaScript Tests:
put_update_playlist_items_2

6. GET Playlist Items
- HTTP method for request:GET.
- Get full details of the items of a playlist owned by a Spotify user.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
get_get_playlist_items_1
get_get_playlist_items_2

JavaScript Tests:
get_get_playlist_items_3
get_get_playlist_items_4

7. DEL Remove Playlist Items
- HTTP method for request:DEL.
- Remove one or more items from a user's playlist.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:
del_remove_playlist_items_1

JavaScript Tests:
del_remove_playlist_items_2

Execution report for the created API collection

Below you can find the execution report that was generated through the Postman collection runner:
run_1
run_2
run_3
run_4

The collection was also run through newman directly from the terminal, and the results can be found below:

newman_collection_1
........................................................................................
Trebuie rezolvate problemele raportate in> 

trebuie sa mai facem un export al colectiei. Mutam fisierul in folderul cu proiect apoi

Alternativ, poți căuta "Command Prompt" în meniul Start și să dai clic pe aplicație.
cmd + enter 
+ calea unde se afla colectia ( click dreapta pe fisier + copiere ca o cale ) + enter

Retesting on the 11.03.2024:

punem poza cum a rulat colectia ( ar trebui sa fie newman_collection_2 ) 

Defects found

EXEMPLU

Issue 1:
There is an AssertionError in the "AddItemInPlaylist" function. The expected status code is 201 Created, but the received status code is 200.

Details:
Error Type: AssertionError
Description: Verify that the Status code is 201 Created.

Steps to Reproduce:

1.Execute the "AddItemInPlaylist" function.
2.Check the returned status code.

Expected Result: The response should have a status code of 201 created.
Actual Result: The response has a status code of 200.
Location: assertion:0 in test-script inside "AddItemInPlaylist"


Conclusions ( formulare concluzii in urma testelor mele facute )

EXEMPLU 
Test Coverage: A comprehensive set of 48 API tests was created, covering diverse functionalities in the Spotify Web API. Tests included various HTTP methods (GET, POST, PUT, DELETE) for thorough coverage.

Test Execution: Successful execution of the entire collection using both Postman's runner and Newman. Detailed execution reports were generated, providing insights into each test case's performance and status.

Functionalities Covered: Extensive testing of playlist operations, item management, artist information retrieval, and playlist following. A variety of scenarios, including positive, negative, and performance testing, were explored.

Issues Identified: Multiple defects were discovered and documented in bug reports. Addressing these issues is crucial before considering a production release to ensure a stable and reliable API.

Lessons Learned: Documentation Impact: Clear documentation on creating access tokens was valuable for establishing a robust testing environment. Collaboration Significance: Continuous collaboration with the development team is vital to align testing efforts with ongoing API changes, ensuring the testing process remains effective and relevant.



