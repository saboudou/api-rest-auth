Api-rest-auth
=========

Installation
------------

<pre><code> # apt install python3-pip
 # apt install sqlite3
 $ pip3 install flask flask-sqlalchemy flask-httpauth
 $ pip3 install -r requirements.txt
</code></pre>
Lancement du serveur
-------
<pre><code> $ python3 api.py</code></pre>


Documentation de l'Api
-----------------

- POST **/api/users**
    
    Permet d'enregistrer un nouvel utilisateur. <br>
    En cas de succès le status code affiché est 201 sinon c'est 400. Un hash du mot de passe est effectué avant l'enregistrement en BDD.

<pre><code>  $ curl -i -X POST -H "Content-Type: application/json" -d '{"username":"yourname","password":"thepass"}' http://127.0.0.1:5000/api/users</code></pre>

- GET **/api/users/&lt;id&gt;**

    Affiche un utilisateur.<br>
    En cas de succès le status code affiché est 200 sinon c'est 400.<br>

<pre><code>  $ curl http://127.0.0.1/users/4 </code></pre>
- GET **/api/token**

    Affiche un token avec un champ `duration` pour la durée de validité.<br>
    En cas de succès c'est le token qui est affiché sinon c'est une erreur 401.<br>
    
<pre><code>  $ curl -u yourname:thepass -i -X GET http://127.0.0.1:5000/api/token</code></pre>


- GET **/api/resource**

    Affiche une ressource protégée.<br>
    
<pre><code>  $ curl -u yourname:thepass -i -X GET http://127.0.0.1:5000/api/resource
</code></pre>

ou

<pre><code>  $ curl -u tyJhbGciOiJIUzI1niIsImV4cCI6MTM4NTY2OTY1NSwiaWF0IjoxMzg1NjY5MDU1fQ.eyJpZCI6MX0.XbOEFJkhjHJ5uRINh2JA1BPzXjSohKYDRT472wGOvjc:x -i -X GET http://127.0.0.1:5000/api/resource</code></pre>

