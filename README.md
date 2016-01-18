# soa-inventoryportal-ear
Primer Commit API soa-inventoryportal

Tanto el EAR del CORE como el EAR del portal requeiren del API soa-inventory-ejbclient.jar para su funcionamiento. 
En este api se encuentran tanto los TO como las interfaces de los servicios.

En este momento se ha determinado el consumo de las interfaces locales de los EJB ya que con la interface remote, sugerencia inicial,
no se estaban transportando correctamente los TO, llegaban null al EJB. Al parecer la invocación de las interfaces remota o locales
tiene implicaciones en el tipo de parámetros que reciben los servicios, en el caso de las remotas el paso de parámetros es por valor, en
el caso de las locales es por referencia.

La configuración del API soa-inventory-ejbclient.jar debe realizarse sobre el jboss en el path:

<JBOSS_HOME>\modules\co\com\qabox\soainv\main

Nótese que se crearon los directorios co-com-qabox-soainv y main. 

En el diredctorio main se debe ubicar el API y se debe crear un archivo llamdo module.xml

<?xml version="1.0" encoding="UTF-8"?>  
<module xmlns="urn:jboss:module:1.1" name="co.com.qabox.soainv">  
       <resources>  
           <resource-root path="soa-inventory-ejbclient.jar"/>  
          </resources>  
</module>  

