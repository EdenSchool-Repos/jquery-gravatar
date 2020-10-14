# jQuery Gravatar

>Un exercice pour manipuler la syntaxe AJAX avec la librairie jQuery

### Énoncé

Par le biais d'un **formulaire**, vous devez requêter directement en méthode `GET` l'image gravatar via github en lui fournissant un id, par ex:

[https://avatars3.githubusercontent.com/u/2439389](https://avatars3.githubusercontent.com/u/2439389)

pour l'afficher dans la div `output` en créant à la volée la balise `<img>`

le tout en jQuery

Vous devez bien récuper le **BINAIRE** (blob) de l'image.
Regardez cette [discussion github](https://github.com/jquery/jquery/issues/4337)

:bulb: Comment associer le `Blob` à l'attribut img src

[createObjectURL](https://developer.mozilla.org/fr/docs/Web/API/File/Using_files_from_web_applications#Exemple_Utilisation_de_l'objet_URLs_pour_afficher_des_images)

```js
var img = document.createElement("img");
img.src = window.URL.createObjectURL([Object de type File, Blob ou MediaSource]);
```

`createObjectURL()` attend Un objet de type `File`, `Blob` ou `MediaSource` pour lequel créer une URL d’objet.


### Indications

- charger la librairie jQuery
- la ressource à requêter est de type **binaire** (blob)
- n'hésitez pas à utiliser les raccourcis jquery
- n'oubliez pas d'annuler l'événement (par défaut) de ~~soumission du formulaire~~

### Paramètre dataType ajax jQuery

:warning: Question, les types blob ou binaire sont-ils présents dans la liste ci-dessous?

dataType (default: Intelligent Guess (xml, json, script, or html))

Type: String
The type of data that you're expecting back from the server. If none is specified, jQuery will try to infer it based on the MIME type of the response (an XML MIME type will yield XML, in 1.4 JSON will yield a JavaScript object, in 1.4 script will execute the script, and anything else will be returned as a string). The available types (and the result passed as the first argument to your success callback) are:

"xml": Returns a XML document that can be processed via jQuery.

"html": Returns HTML as plain text; included script tags are evaluated when inserted in the DOM.

"script": Evaluates the response as JavaScript and returns it as plain text. Disables caching by appending a query string parameter, _=[TIMESTAMP], to the URL unless the cache option is set to true. Note: This will turn POSTs into GETs for remote-domain requests.

"json": Evaluates the response as JSON and returns a JavaScript object. Cross-domain "json" requests that have a callback placeholder, e.g. ?callback=?, are performed using JSONP unless the request includes jsonp: false in its request options. The JSON data is parsed in a strict manner; any malformed JSON is rejected and a parse error is thrown. As of jQuery 1.9, an empty response is also rejected; the server should return a response of null or {} instead. (See json.org for more information on proper JSON formatting.)

"jsonp": Loads in a JSON block using JSONP. Adds an extra "?callback=?" to the end of your URL to specify the callback. Disables caching by appending a query string parameter, "_=[TIMESTAMP]", to the URL unless the cache option is set to true.

"text": A plain text string.
multiple, space-separated values: As of jQuery 1.5, jQuery can convert a dataType from what it received in the Content-Type header to what you require. For example, if you want a text response to be treated as XML, use "text xml" for the dataType. You can also make a JSONP request, have it received as text, and interpreted by jQuery as XML: "jsonp text xml". Similarly, a shorthand string such as "jsonp xml" will first attempt to convert from jsonp to xml, and, failing that, convert from jsonp to text, and then from text to xml.
