## Integracion Wazuh + Jira

1. Se debe crear el script "custom-jira" en la ruta "/var/ossec/integrations/" del servidor wazuh.

2. Es necesario tener una cuenta de jira cloud creada y configurada con el tipo de issue que se quiere generar, en este caso se genero un issue del tipo incidente, luego es necesario obtener el Jira Key que se muestra en la URL, en este caso es POC, y por ultimo el tipo de issue que se obtiene desde tipos de incidencias.

https://devcode.atlassian.net/jira/software/projects/"POC"/boards/12

https://devcode.atlassian.net/jira/software/projects/POC/settings/issuetypes/"10057"

3. Una vez obtenidos los valores necesarios para agregar al script se debe obtener el API KEY de Jira para poder autenticar nuestro script. Esto se obtiene generando la key desde la siguiente URL.

https://id.atlassian.com/manage-profile/security/api-tokens

4. Luego le damos los permisos necesarios al archivo creado custom-jira ejecutando los siguientes comandos como administrador:

chmod 750 custom-jira
chown root:wazuh custom-jira

5. Por ultimo, agregamos el siguiente codigo en el settings de wazuh.

<integration>
  <name>custom-jira</name>
  <hook_url>"agregar url de Jira cloud"/rest/api/3/issue/</hook_url>
  <api_key>"agregar email":"agregar token"</api_key>
  <alert_format>json</alert_format>
</integration>