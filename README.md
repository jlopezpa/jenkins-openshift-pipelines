# Jenkisn-Openshift-Pipelines
Esta es una repo para realizar la creación eliminación de recursos en Openshift utilizando Pipelines de Jenkins

## Comenzando ���


Mira **Resources** para conocer como desplegar el proyecto.


### Pre-requisitos ���

```
1.- Disponer de un OCP Cluster OpenShift v 3.11 + 4.x
2.- Crear un RG para realizar la prueba
3.- Instalar el operador que gestiona la pilas hacia Jenkins
4.- Crear un script para ejecutar la creación de un resource o app en una pipeline en Jenkins
5.- Validar la creación del recurso deacuerdo a las necesidades.

```

### Instalación del Operador ���

Comandos oc para ejecutar la instalación del **Operador**
```
./oc.exe apply -f /operador/Red_Hat_OpenShift_Pipelines_Operator.yaml

```
Verificar si se se creo correctamente el serviceaccount sa y la subs. 
```
./oc.exe get sa
./oc.exe get subs -n  namespace
./oc.exe describe subs -n namespace

```

Obtener el nombre del cluster de OCP
```
./oc.exe config view --minify -o jsonpath={.clusters[0].cluster.server

```

Obtener plantillas de Openshift

```
./oc.exe get templates -n openshift

```

Verifica que la url de Jenkins esta en funcionamiento **https://jenkins-{name-account}-dev.apps.sandbox.x8i5.p1.openshiftapps.com/**


## Ejecutando  Pipelines en Jenkis Test  ⚙️

Desde la Web -> **https://jenkins-{name-account}-dev.apps.sandbox.x8i5.p1.openshiftapps.com/** -> Log in with OpenShift -> Nueva Tarea -> Pipeline -> Ingrese el Nombre -> Copy el contenido  /resource/*.json y luego Guardar

### Analice las pruebas end-to-end ���
Desde el Pipeline Advanced Project Option -> Pipelinescript ingrese:

```

pipeline {
    agent any

        stages {
	        stage('Hello') {
		            steps {
			                    echo 'Hello World'
			          }
			       }
		 }
	   }


```

## Despliegue <dce6>
Para ejecutar las pruebas se debe ir a la Opcion Contruir Ahora si todo marcha OK entonces se puede ver el Historial de Tareas en verde 
```
Started by user javier
Running in Durability level: MAX_SURVIVABILITY
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/jobs/demo/workspace
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Hello)
[Pipeline] echo
Hello World
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```
_


## Autores ✒️
_

* **Javier López** - *Trabajo Inicial* - [javier](https://github.com/jlopezpa/jenkins-openshift-pipelines.git)
* **Openshift** - *Documentación* - [doc](https://docs.openshift.com/container-platform/4.8/cicd/pipelines/creating-applications-with-cicd-pipelines.html)
                                         (https://docs.openshift.com/container-platform/4.8/cicd/pipelines/working-with-pipelines-using-the-developer-perspective.html)

## Licencia 
De uso Libre

