# simple_flask
simple repo demonstrating flask, luguru, etc

## Dependencies
Dependencies are kept to minimum. That said, we wholeheartedly embrace the following
* loguru

## References
The following resources were useful during the creation of this project

* https://ayumitanaka13.medium.com/how-to-use-ajax-with-python-flask-729c0a8e5346

## Fetch ? 
Fetch is the standards compliant followup to XMLHttpRequest. It works thusly:

### Fetch (client)
This runs in the browser
``` js
function getHello() {
    const url = 'http://localhost:8989/hello'
    fetch(url)
    .then(response => response.json())  
    .then(json => {
        console.log(json);
        document.getElementById("demo").innerHTML = JSON.stringify(json)
    })
}
```
### Fetch (server)
From the programmers perspective, all we do to handle fetch() calls is return JSON instead of HTML.
This mostly makes sense, since the server really is just responding to another GET request.
I actually wish you could make this a little more explicit. But maybe thats cuz I'm a noob.

``` py
@app.route('/hello', methods=['GET'])
def hello():
    @after_this_request
    def add_header(response):
        response.headers.add('Access-Control-Allow-Origin', '*')
        return response

    jsonResp = {'jack': 4098, 'sape': 4139}
    print(jsonResp)
    return jsonify(jsonResp)
```

