The same way you can specify a response model, you can also declare the HTTP status code used for the response with the parameter `status_code` in any of the path operations:

* `@app.get()`
* `@app.post()`
* `@app.put()`
* `@app.delete()`
* etc.

```Python hl_lines="6"
{!./src/response_status_code/tutorial001.py!}
```

!!! note
    Notice that `status_code` is a parameter of the "decorator" method (`get`, `post`, etc). Not of your path operation function, like all the parameters and body.

The `status_code` parameter receives a number with the HTTP status code.

It will:

* Return that status code in the response.
* Document it as such in the OpenAPI schema (and so, in the user interfaces):

<img src="/img/tutorial/response-status-code/image01.png">


## About HTTP status codes

!!! note
    If you already know what HTTP status codes are, skip to the next section.

In HTTP, you send a numeric status code of 3 digits as part of the response.

These status codes have a name associated to recognize them, but the important part is the number.

In short:

* `100` and above are for "Information". You rarely use them directly.
* **`200`** and above are for "Successful" responses. These are the ones you would use the most.
    * `200` is the default status code, which means everything was "OK".
    * Another example would be `201`, "Created". It is commonly used after creating a new record in the database.
* `300` and above are for "Redirection". 
* **`400`** and above are for "Client error" responses. These are the second type you would probably use the most.
    * An example is `404`, for a "Not Found" response.
    * For generic errors from the client, you can just use `400`.
* `500` and above are for server errors. You almost never use them directly. When something goes wrong at some part in your application code, or server, it will automatically return one of these status codes.

!!! tip
    To know more about each status code and which code is for what, check the <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Status" target="_blank"><abbr title="Mozilla Developer Network">MDN</abbr> documentation about HTTP status codes</a>.


## Shortcut to remember the names

Let's see the previous example again:

```Python hl_lines="6"
{!./src/response_status_code/tutorial001.py!}
```

`201` is the status code for "Created".

But you don't have to memorize what each of these codes mean.

You can use the convenience variables from `starlette.status`.

```Python hl_lines="2 7"
{!./src/response_status_code/tutorial002.py!}
```

They are just a convenience, they hold the same number, but that way you can use the editor's autocomplete to find them:

<img src="/img/tutorial/response-status-code/image02.png">
