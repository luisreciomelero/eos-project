# EOS Project

El ejercicio consiste en 3 tareas principales:


1. Automatización de la creación de un número de namespaces cuyo nombre siga el patrón eos-#.
2. Despliegue de un deployment en cada namespace con un número de replicas igual al número de su namespace. Es decir, eos-3 tedría 3 replicas en el deployment. También se ha incluido la salvedad de que se le indique un número máximo de replicas, por ejemplo 3, de esta forma el namespace eos-1 tendrá una replica, eos-2 tendrá dos, eos-3 tendrá 3, eos-4 tendrá 3, eos-5 tendrá 3, etc.
3. Por último, se ha incluido la tarea de generar un fichero, si no existiese, en el que se escriban los pods creados junto a sus namespaces. De la siguiente forma:

                            Pod -> eos-app-b4fbf46f8-t9mbw, Namespace -> eos-1
                            Pod -> eos-app-b4fbf46f8-4chv2, Namespace -> eos-2
                            Pod -> eos-app-b4fbf46f8-h4qcq, Namespace -> eos-2
                            Pod -> eos-app-b4fbf46f8-5cqfc, Namespace -> eos-3
                            Pod -> eos-app-b4fbf46f8-6txvc, Namespace -> eos-3
                            Pod -> eos-app-b4fbf46f8-jp6wx, Namespace -> eos-3


La estructura del proyecto consta de un playbook, playbook.yaml, ubicado en la raiz del repositorio y un role, ubicado en el directorio roles/deploy.

## Implementación

Para la realización de las tareas se ha optado por definir un role con estas, parametrizadas, e iterar para evitar la definición de tareas repetitivas. Estas tareas se encuentran definidas en **/roles/deploy/tasks/main.yaml**

La limitación de máximas replicas por deployment se ha configurado a partir de la variable **max_instances** definida en el fichero **playbook.yaml**. En caso de no estar definida, se crearán tantas replicas como número tenga el namespace.

## Observaciones
El proyecto se han realizado bajo las versiones:

 - Kubernetes: 1.25
 - Ansible: 2.13.6
 - Python: 3.8.10
 - Jinja: 3.1.2

Para la probar el correcto funcionamiento del playbook se ha optado por utilizar el playground de Killercoda con la versión de Kubernetes 1.25 (https://killercoda.com/playgrounds/scenario/kubernetes), sobre la que se ha instalado Ansible.

## Problemas encontrados

En primera instancia, la creación de los deployment en cada namespace se pensó realizar mediante el módulo de kubernetes, al igual que la creación del namespace, sin embargo, al iterar sobre el número de namespaces requerido y tratar de declarar el número de replicas sobre la definición del deployment mediante una expresión jinja2, el resultado era de error al no poder incluir un string como número de replicas.

La solución adoptada ha sido la creación de los deployment mediante el módulo command de ansible.

En posteriores iteraciones sería necesario modificar la forma de creación del deployment y encontrar una solución que permita utilizar la creación de los deployment con el módulo de kubernetes.
