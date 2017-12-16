# Errors

The IdeaBox API uses the following error codes:

| Error Code | Meaning                                                                                   |
| ---------- | ----------------------------------------------------------------------------------------- |
| 400        | Bad Request -- Your request sucks.                                                        |
| 401        | Unauthorized -- Your API key is wrong.                                                    |
| 403        | Forbidden -- The kitten requested is hidden for administrators only.                      |
| 404        | Not Found -- The specified kitten could not be found.                                     |
| 405        | Method Not Allowed -- You tried to access a kitten with an invalid method.                |
| 406        | Not Acceptable -- You requested a format that isn't json.                                 |
| 409        | CONFLICT -- The specified request already exists or conflicts with an existing parameter. |
| 500        | Internal Server Error -- We had a problem with our server. Try again later.               |
