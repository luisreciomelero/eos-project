# EOS Project

El ejercicio consiste en 3 tareas principales:
1. Automatización de la creación de un número de namespaces cuyo nombre siga el patrón eos-#.
2. Despliegue de un número de deployments en cada namespace igual al número de su namespace. Es decir, eos-3 tedría 3 deployment. También se ha incluido la salvedad de que se le indique un número máximo de deployments, por ejemplo 3, de esta forma el namespace eos-1 tendrá un deployment, eos-2 tendrá dos, eos-3 tendrá 3, eos-4 tendrá 3, eos-5 tendrá 3, etc.
3. Por último, se ha incluido la tarea de generar un fichero, si no existiese, en el que se escriban los pods creados junto a sus namespaces. De la siguiente forma:

                            Pod -> eos-app-b4fbf46f8-t9mbw, Namespace -> eos-1
                            Pod -> eos-app-b4fbf46f8-4chv2, Namespace -> eos-2
                            Pod -> eos-app-b4fbf46f8-h4qcq, Namespace -> eos-2
                            Pod -> eos-app-b4fbf46f8-5cqfc, Namespace -> eos-3
                            Pod -> eos-app-b4fbf46f8-6txvc, Namespace -> eos-3
                            Pod -> eos-app-b4fbf46f8-jp6wx, Namespace -> eos-3


La estructura del proyecto consta de un playbook, playbook.yaml, ubicado en la raiz del repositorio y un role, ubicado en el directorio roles/deploy.

## Observaciones

