# Endpoint testing of the Spotify Music App with Postman

### For security reasons user_id, client_secret and client_id have been removed from the project, please use your own credentials

<a href="https://open.spotify.com/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/2048px-Spotify_logo_without_text.svg.png" alt="spotify" width="200" height="200"/></a>

## Pre-requisites:

 - fork this collection in Postman, make sure to select environment `spotify env`
 - create or use an existing Spotify account (go to `https://www.spotify.com/es/account/overview/` and copy Username, after past it to the environment variable `spotify env` in user_id field)
 - create a spotify app `https://developer.spotify.com/dashboard/applications`, inside new app hit the `edit settings button` and add this: `https://oauth.pstmn.io/v1/browser-callback` to `RedirectURIs` field, click add button, save changes.
 - copy `client id` and `client secret` from the newly created Spotify app and add them both to `spotify env` in respective fields
 - inside the collection open the authorization tab and generate a new access token, make sure that notification hasn’t been blocked in your browser

## Well done, now you are all set and can run all tests

[![Run in Postman](https://run.pstmn.io/button.svg)](https://god.gw.postman.com/run-collection/23524391-c069d2f4-4858-4df5-a6c9-4f353823c0b8?action=collection%2Ffork&collection-url=entityId%3D23524391-c069d2f4-4858-4df5-a6c9-4f353823c0b8%26entityType%3Dcollection%26workspaceId%3Dbfaf19bf-cb6b-4016-93b7-65e73bb056db#?env%5BSpotify%20env%5D=W3sia2V5IjoiQ2xpZW50IElEIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiZGVmYXVsdCIsInNlc3Npb25WYWx1ZSI6IjM2MWUzZDc2OWZmYTRmODhhNzJkMTJiOWU4NTQzZDA2Iiwic2Vzc2lvbkluZGV4IjowfSx7ImtleSI6IkNsaWVudCBTZWNyZXQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJkZWZhdWx0Iiwic2Vzc2lvblZhbHVlIjoiMjEzMmQxZWIyNGRmNGJkZmIzYjRjNWE5MTlkY2FjOTIiLCJzZXNzaW9uSW5kZXgiOjF9LHsia2V5IjoiYXJ0aXN0SWQiLCJ2YWx1ZSI6IjRkcEFSdUh4bzUxRzN6NzY4c2duclkiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiYW55Iiwic2Vzc2lvblZhbHVlIjoiNGRwQVJ1SHhvNTFHM3o3NjhzZ25yWSIsInNlc3Npb25JbmRleCI6Mn0seyJrZXkiOiJ1c2VyX2lkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIzMXo3ZWptenp2eDV3Z3Fpa3p2NHRmdzd4Mnd5Iiwic2Vzc2lvbkluZGV4IjozfSx7ImtleSI6InBsYXlsaXN0X2Rlc2NyaXB0aW9uIiwidmFsdWUiOiJCZXN0IG9mIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6ImRlZmF1bHQiLCJzZXNzaW9uVmFsdWUiOiJCZXN0IG9mIiwic2Vzc2lvbkluZGV4Ijo0fSx7ImtleSI6ImFydGlzdCIsInZhbHVlIjoiQWRlbGUiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiZGVmYXVsdCIsInNlc3Npb25WYWx1ZSI6IkFkZWxlIiwic2Vzc2lvbkluZGV4Ijo1fSx7ImtleSI6InBsYXlsaXN0X2lkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiYW55Iiwic2Vzc2lvblZhbHVlIjoiMVB2bDVpVVFMbTJkVHA1Qkt6WmJxVyIsInNlc3Npb25JbmRleCI6Nn0seyJrZXkiOiJkZXNpcmVkX3RyYWNrIiwidmFsdWUiOiJSb2xsaW5nIGluIHRoZSBEZWVwIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6ImRlZmF1bHQiLCJzZXNzaW9uVmFsdWUiOiJSb2xsaW5nIGluIHRoZSBEZWVwIiwic2Vzc2lvbkluZGV4Ijo3fSx7ImtleSI6InRyYWNrVXJpIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiYW55Iiwic2Vzc2lvblZhbHVlIjoic3BvdGlmeTp0cmFjazo0T1NCVFlXVndzUWhHTEY5Tkh2SWJSIiwic2Vzc2lvbkluZGV4Ijo4fSx7ImtleSI6ImJhc2VVUkwiLCJ2YWx1ZSI6Imh0dHBzOi8vYXBpLnNwb3RpZnkuY29tL3YxIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiaHR0cHM6Ly9hcGkuc3BvdGlmeS5jb20vdjEiLCJzZXNzaW9uSW5kZXgiOjl9LHsia2V5IjoibmV3X3BsYXlsaXN0X3RpdGxlIiwidmFsdWUiOiJBZGVsZSAyNSIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJkZWZhdWx0Iiwic2Vzc2lvblZhbHVlIjoiQWRlbGUgMjUiLCJzZXNzaW9uSW5kZXgiOjEwfV0=)

## Brief logical explanation of the testing flow:

- GET request for `Search artists and songs` were implemented to save artists id to env variable, and able to search through top tracks. Status code and variable assertions were added.
- GET request for `Top tracks` to get track from the env variables that user like to add (if you would like to change track or artist just go to `spotify env` and add your personal choice. Thought all test env variables were used to make scenarios dynamic). Also logic were added to loop through the response body and extract track URI for farther implementation of test scenario. Status code and variable assertions were added.
- 
 



