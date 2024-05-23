# Projecte UF3 de M04

*Objectiu del projecte: Desenvolupar una aplicació amb python + flask que mostra el contingut de XMLs en format feed/rss maquetat amb bootstrap.

Contingut per explicar:
1. Entorns virtuals a python (.venv).
2. Flask, conceptes bàsics. No farem formularis ni res complex, tan sols peticions get.
3. Jinja, el sistema de plantilles de flask. Com mostrar variables, if & for. No cal res més.
4. Com recuperar les dades d'un fitxer RSS fent servir la llibreria feedparser.
5. Bootstrap 5.
6. Conceptes bàsics de javascript.

## Entorns Virtuals

* Que son?

Un entorn virtual és un mecanisme que permet crear un espai aïllat per a la instal·lació de paquets i dependències d'un projecte específic en Python. Això és especialment útil per gestionar diferents versions de llibreries i evitar conflictes entre projectes que poden tenir diferents requisits.

* Per començar a treballar amb un entorn virtual, el primer pas és crear-lo. Per això, obre un terminal integrat des del Visual Code i executa:

```
Amb linux: python3 -m venv .venv

Amb windows: python -m venv .venv
```
* El següent pas és activar-lo. Per això executa:

```
Amb linux: source .venv/bin/activate

Amb Windows: .venv\Scripts\activate
```

* Ara podem observar que ja som dins de l'entorn al prompt

![image](https://github.com/harcosm/projectom4/assets/130600270/d82c86f9-97af-4206-8ca4-dbb5b44f1e2d)

* Ara ja pots instal·lar els paquets que necessitis, com són:

  ```
    pip install flask
	  pip install feedparser
  ```
* Per sortir de l'entorn virtual, executa:
  ```
  deactivate
  ```
* Finalment, per a Visual Code l'extensió Python Environment Manager facilita la integració entre el Visual Code i l'entorn virtual.

  Aqui os deixo el seguent Link per poder baixarse l'extensió: https://marketplace.visualstudio.com/items?itemName=donjayamanne.python-environment-manager
  
Per qualsevol dubte amb Entorns Virtuals podeu consultar al seguent link: https://docs.python.org/es/3/library/venv.html  




## Flask 
* Que es Flask?

Flask és un microframework per a Python que permet desenvolupar aplicacions web de manera senzilla i flexible. Va ser creat per Armin Ronacher com a part del projecte Pocoo i és conegut per la seva simplicitat i extensibilitat.

* Per inicial l'aplicació cal executar des del terminal integrat del Visual Code:
```
flask run --debug
```
Aqui us deixo un petit exemple per inicialitzar Flask:

![image](https://github.com/harcosm/projectom4/assets/130600270/f947087b-dacc-4b34-af3a-95968a068aab)

## Jinja

* Que es Jinja?

Jinja és un motor de plantilles per a Python, dissenyat per a generar dinàmicament HTML, XML, o altres formats de sortida en aplicacions web. Jinja és molt utilitzat juntament amb frameworks web com Flask i Django, tot i que també pot ser utilitzat de manera independent. Va ser creat per Armin Ronacher, el mateix creador de Flask.

* Conceptes bàsics:


1. Variables.

   Pots inserir variables a les plantilles utilitzant les doble claus ({{ }}):

   ```
   <p>Hola, {{ nom }}!</p>
   ```

2. Control de flux.

   Jinja permet utilitzar estructures de control com bucles i condicions dins de les 	 
   plantilles.

* Bucles:
  
```
<ul>
  {% for article in articles %}
    <li>{{ article.titol }}</li>
  {% endfor %}
</ul>
```

* Condicions:
```
{% if user %}
  <p>Hola, {{ user.nom }}!</p>
{% else %}
  <p>Hola, convidat!</p>
{% endif %}
 ```

3. Filtres.

Els filtres permeten modificar la sortida de les variables. Per exemple, per convertir un text a majúscules:

```
<p>{{ nom | upper }}</p>
```
4. Macros.
Les macros són com funcions dins de les plantilles, que permeten reutilitzar codi.
```
{% macro saludo(nom) %}
  <p>Hola, {{ nom }}!</p>
{% endmacro %}

{{ saludo('Anna') }}
```

* Exemple complet
A continuació es mostra un exemple complet d'una aplicació Flask que utilitza Jinja per renderitzar plantilles HTML:


app.py:
```
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
    user = {'nom': 'Anna'}
    articles = [
        {'titol': 'Article 1'},
        {'titol': 'Article 2'},
        {'titol': 'Article 3'}
    ]
    return render_template('index.html', user=user, articles=articles)

if __name__ == '__main__':
    app.run(debug=True)
```


templates/index.html:
```
<!DOCTYPE html>
<html>
<head>
    <title>Benvingut</title>
</head>
<body>
    {% if user %}
        <h1>Hola, {{ user.nom }}!</h1>
    {% else %}
        <h1>Hola, convidat!</h1>
    {% endif %}

    <h2>Articles</h2>
    <ul>
        {% for article in articles %}
            <li>{{ article.titol }}</li>
        {% endfor %}
    </ul>
</body>
</html>
```

## RSS

* Que es?

L'estàndard RSS és un format XML mitjançant el qual portals com diaris, blogs o podcasts comparteixen el seu contingut per a que es faci servir en altres llocs webs o programes.












  
   
   

   
   













  
  






