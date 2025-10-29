# talleres AI 

## Guía 1 — Hello World AI con Python y la API de OpenAI

Curso:	IA	en	el	Aula	— Nivel	Avanzado		

Profesor:	Luis	Daniel	Benavides	Navarro

Fecha:	22	de	octubre	de	2025

Esta	guía	introduce	los	conceptos	básicos	para	conectarse	a	un	modelo	de	lenguaje	de

Esta	guía	introduce	los	conceptos	básicos	para	conectarse	a	un	modelo	de	lenguaje	de	
OpenAI	usando	Python.	El	objetivo	es	construir	un	entorno	funcional,	comprender	la	
estructura	de	la	API	y	ejecutar	un	ejemplo	tipo	'Hello	World'	con	inteligencia	artificial.

1. Requisitos previos
Antes	de	comenzar,	asegúrese	de	cumplir	los	siguientes	requisitos:
• Python	3.10	o	superior	instalado	en	su	equipo.
• Cuenta	activa	en	la	plataforma	de	OpenAI.
• Conexión	a	Internet.
• Editor	de	texto	o	entorno	como	Visual	Studio	Code	o	Jupyter	Notebook.
2. Creación del entorno virtual
Se	recomienda	crear	un	entorno	virtual	de	Python	para	aislar	las	dependencias	del	
proyecto.	Ejecute	los	siguientes	comandos	en	su	terminal	o	consola:

```
# Crear carpeta de trabajo
mkdir hello_ai
cd hello_ai
```

```
# Crear entorno virtual
python -m venv venv
```
```
# Activar el entorno virtual
# En Windows:
venv\Scripts\activate
# En macOS/Linux:
source venv/bin/activate
```

```
# Instalar dependencias
pip install openai python-dotenv
```

3. Configuración de la clave API
La	API	de	OpenAI	requiere	autenticación	mediante	una	clave	personal.	Cree	un	archivo

```
OPENAI_API_KEY=su_clave_aqui

```

4. Primer script: Hello World AI
Cree	un	archivo	llamado	`hello_ai.py`	con	el	siguiente	contenido:

``` python
import os
from openai import OpenAI
from dotenv import load_dotenv
# Cargar variables de entorno
load_dotenv()
# Inicializar cliente con la clave API
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))
# Solicitud al modelo
prompt = "Escribe un saludo tipo 'Hello World' con un toque creativo de IA."
response = client.chat.completions.create(
 model="gpt-4o-mini",
 messages=[{"role": "user", "content": prompt}],
 temperature=0.6
)
# Mostrar respuesta
print("Respuesta del modelo:")
print(response.choices[0].message.content)

```

Salida:

![alt text](assets\salidaTaller1.png)


5. Explicación del código
A	continuación	se	explica	el	propósito	de	cada	bloque	del	script:

    1. Importaciones:	se	usan	las	librerías	os,	dotenv	y	openai	para	manejar	variables	de	
    entorno	y	conectarse	a	la	API.
    2. `load_dotenv()`:	carga	la	clave	API	almacenada	en	el	archivo	`.env`.
    3. Inicialización	del	cliente:	crea	una	instancia	de	conexión	con	la	API	mediante	
    `OpenAI(api_key=...)`.
    4. `prompt`:	texto	de	entrada	enviado	al	modelo.	En	este	caso,	una	instrucción	simple	tipo	
    'Hello	World'.
    5. `temperature`:	controla	la	creatividad	de	la	respuesta.	Valores	bajos	(0.1–0.3)	hacen	
    salidas	más	predecibles;	valores	altos	(0.7–1.0)	aumentan	la	variabilidad.
    6. `response.choices[0].message.content`:	obtiene	el	texto	generado	por	el	modelo.

6. Ejecución del programa
    Una	vez	configurado	el	entorno	y	creado	el	archivo	`hello_ai.py`,	ejecute	el	siguiente	
    comando	en	la	terminal:
    python hello_ai.py
    El	modelo	responderá	con	un	mensaje	tipo	'Hello	World'	generado	por	IA.	Por	ejemplo:	
    '¡Hola	mundo!	Hoy	la	inteligencia	artificial	también	quiere	saludarte.'

7. Conclusión
    Ha	completado	su	primera	conexión	a	la	API	de	OpenAI.	En	las	próximas	guías	aprenderá	a estructurar	salidas	en	JSON,	automatizar	tareas	docentes	y	crear	asistentes	personalizados


## Guía 2 — Hello World AI en Jupyter Notebook en VS Code

Curso:	IA	en	el	Aula	— Nivel	Avanzado		

Profesor:	Luis	Daniel	Benavides	Navarro

Fecha:	22	de	octubre	de	2025

Esta	guía	explica	cómo	crear	un	proyecto	de	inteligencia	artificial	desde	Visual	Studio	Code (VS	Code),	configurando	el	entorno	Jupyter,	conectándose	a	la	API	de	OpenAI	y	ejecutando	un	ejemplo	'Hello	World	AI'.	Todo	el	proceso	se	realiza	dentro	de	VS	Code,	sin	usar	la	terminal	externa.

1. Requisitos previos
    * Visual	Studio	Code	instalado	(versión	1.85	o	superior).
    * Extensiones	instaladas:	Python	(Microsoft)	y	Jupyter	(Microsoft).
    * Python	3.10	o	superior	instalado	en	su	equipo.
    * Cuenta	y	clave	API	de	OpenAI.
    * Conexión	a	Internet	estable.

2. Crear carpeta del proyecto desde VS Code
    1.	Abra	Visual	Studio	Code.
    2.	En	el	menú	superior,	seleccione	**File	>	Open	Folder...**	y	elija	la	ubicación	donde	desea	
    crear	su	proyecto.
    3.	Cree	una	nueva	carpeta	llamada	**hello_ai_vscode**	y	ábrala

3. Crear y activar el entorno virtual dentro de VS Code
    1.	Abra	el	panel	de	comandos	con	**Ctrl+Shift+P**	(Windows/Linux)	o	**Cmd+Shift+P**	
    (macOS).
    2.	Escriba	**Python:	Create	Environment**	y	presione	*Enter*.
    3.	Seleccione	el	tipo	de	entorno	**Venv**.
    4.	Elija	el	intérprete	de	Python	(por	ejemplo,	Python	3.10).
    5.	Espere	a	que	VS	Code	cree	el	entorno	automáticamente.
    6.	Acepte	el	mensaje	que	ofrece	activar	el	entorno	en	el	proyecto.

4. Instalar dependencias desde el terminal integrado
    Abra	el	terminal	integrado	con	**Ctrl+Ñ**	o	desde	**View	>	Terminal**	y	ejecute	los	
    siguientes	comandos:
    
    ```
    pip install openai python-dotenv jupyter ipykernel
    python -m ipykernel install --user --name hello_ai_vscode
    ```

    Crear un archivo Jupyter Notebook para instalar y configurar dependencias:

    En	lugar	de	usar	la	terminal,	puede	instalar	todas	las	dependencias	directamente	desde	un	archivo	Jupyter	Notebook	dentro	de	VS	Code.

    1. .	Presione	**Ctrl+Shift+P**	y	seleccione	**Jupyter:	Create	New	Jupyter	Notebook**.
    2.	Guarde	el	archivo	como	**setup_hello_ai.ipynb**	dentro	de	la	carpeta	del	proyecto.
    3.	En	la	parte	superior	derecha,	seleccione	el	kernel	correspondiente	al	entorno	que	creó (**hello_ai_vscode**).
    4.	Cree	una	primera	celda	con	los	siguientes	comandos	para	instalar	las	librerías	necesarias:

    %pip install openai python-dotenv 

    VSCode	le	pedirá	instalar	las	librerías	de	jupyter	en	su	entorno	“.venv”,	autorice	la instalación.	

    Una	vez	completada	la	instalación,	el	entorno	quedará	configurado	y	podrá	ejecutar	celdas de	código	Python	dentro	del	mismo	notebook.

5. Configurar la clave API (.env)
    1.	En	el	explorador	lateral	de	VS	Code,	haga	clic	derecho	en	la	carpeta	del	proyecto	y	
    seleccione	**New	File**.
    2.	Nombre	el	archivo	como	`.env`.
    3.	Agregue	la	siguiente	línea	(reemplace	con	su	propia	clave):
    OPENAI_API_KEY=su_clave_aqui
    4.	Guarde	el	archivo.	VS	Code	cargará	automáticamente	las	variables	del	`.env`	en	su	entorno	
    cuando	ejecute	código.
    5.	No	suba	este	archivo	a	GitHub	ni	lo	comparta	públicamente

6. Crear y configurar el Notebook en VS Code
    1.	Presione	**Ctrl+Shift+P**	y	ejecute	el	comando	**Jupyter:	Create	New	Jupyter	
    Notebook**.
    2.	Guarde	el	archivo	como	**hello_ai.ipynb**	dentro	de	la	carpeta	del	proyecto.
    3.	En	la	parte	superior	derecha,	seleccione	el	kernel	correspondiente	al	entorno	creado	
    (**hello_ai_vscode**).
    4.	Verifique	que	la	barra	inferior	muestre	el	entorno	activo.

7. Celdas principales del notebook
    Celda 1 — Importación y configuración del entorno

    ``` python
    import os
    from dotenv import load_dotenv
    from openai import OpenAI
    load_dotenv()
    client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))
    print("Cliente OpenAI inicializado correctamente.")
    ```

    Celda 2 — Ejemplo Hello World AI

    ``` python
    prompt = "Escribe un saludo tipo 'Hello World' con un toque creativo de IA."
    resp = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[{"role": "user", "content": prompt}],
    temperature=0.6
    )
    print(resp.choices[0].message.content)
    ```

8. 	pruebas de distintas configuraciones	de	`temperature`	y	`max_tokens`.	

    ``` python
    for t in [0.3, 0.5, 0.9]:
    response = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[{"role": "user", "content": "Describe brevemente qué es la IA."}],
        temperature=t,
        max_tokens=35
    )
    print(f"--- temperature={t} ---")
    print(response.choices[0].message.content)
    ```

