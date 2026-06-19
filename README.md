# CURL with Vim

[![asciicast](https://asciinema.org/a/1257605.svg)](https://asciinema.org/a/1257605)

Example rest api calls:

```
--url https://openlibrary.org/api/books?bibkeys=ISBN:0201558025,LCCN:93005405&format=json

# or the same as above using --url-query
--url https://openlibrary.org/api/books
--url-query bibkeys=ISBN:0201558025,LCCN:93005405
--url-query format=json

--url https://api.sunrise-sunset.org/json?lat=36.7201600&lng=-4.4203400

# or the same as above using --url-query
--url https://api.sunrise-sunset.org/json
--url-query lat=36.7201600
--url-query lng=-4.4203400

# --jq is not curl parameter. If added, curl output would be piped through jq
--url https://httpbin.org/post
--header "Content-Type: application/json"
--jq
--data
{
"string": "hello world",
"number": 69,
"date": "2024-04-09"
}
```

Common parameters for the rest of `--url`:

```
--$url https://dog.ceo/api
--$header "Content-Type: application/json"
--$jq

--url /breeds/list/all

--url /breed/hound/images
```

Collibra queries example:

```
--$url https://somecustomer-test.collibra.com/rest/2.0
--$user username:password@12345
--$jq

# Get community
--url /communities
--url-query name=6. Governance
--url-query nameMatchMode=EXACT

# Get domain
--url /domains
--url-query name=Data Policy Register
--url-query nameMatchMode=EXACT
```

## cURL

There is a single command `:Curl` that creates and runs `curl` cli-command out
of text under the cursor.

If `:Curl!` is used, the `curl` cli-command is copied to `+` register (clipboard).


## Additional setup

One can add mappings to `~/.vim/after/ftplugin/curl.vim`:

```
nnoremap <buffer> <space><space>r :Curl<CR>
xnoremap <buffer> <space><space>r :Curl<CR>
```
