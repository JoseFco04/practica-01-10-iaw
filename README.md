# Practica-01-10-IAW Jose Francisco León López
## En esta práctica vamos a usar la práctica 9 y vamos a crear dos máquinas virtuales en Amazon una que va a ser un balanceador y la otra que va a ser un nuevo front-end. 
## El objetivo de la práctica es que en el dominio que tenemos creado cada vez que recarguemos la página se vayan intercambiando los dos frontales.
## Para hacer la práctica necesitamos crear dos máquinas nuevas en Amazon. La primera la del balanceador con su respectivo grupo de seguridad creado .
![1](https://github.com/JoseFco04/practica-01-10-iaw/assets/145347148/231dc3ca-9d92-4c39-8c34-70d56a8e5cbd)
![2](https://github.com/JoseFco04/practica-01-10-iaw/assets/145347148/5ae48cd6-17a2-4ce1-bf31-7ba29fd9d326)

## Y también una máquina nueva con el segundo frontend que se vería así :
![3](https://github.com/JoseFco04/practica-01-10-iaw/assets/145347148/e2b8d2f0-d5ce-496f-97ef-30f3fe488124)
![4](https://github.com/JoseFco04/practica-01-10-iaw/assets/145347148/6ad76e5a-4bf7-4d62-a0e1-8db2a67ef46f)

### En la máquina del balanceador vamos a ejecutar el script de install_load_balancer para instalar el balanceador en la máquina. Este script paso a paso se ve así:
#### Mostramos todos los comandos que se van ejecutando
~~~
set -ex
~~~
#### Actualizamos los repositorios
~~~
apt update
~~~
#### Actualizamos los paquetes
~~~
#apt upgrade -y
~~~
#### Importamos el archivo de variables 
~~~
source .env
~~~
#### Instalamos el servidor web Apache
~~~
sudo apt install apache2 -y
~~~
#### Habilitamos los módulos necesarios para configurar Apache como proxy inverso
~~~
a2enmod proxy
a2enmod proxy_http
a2enmod proxy_balancer
~~~
#### Para activar este método de balance tenemos que activar el módulo lbmethod_byrequests:
~~~
a2enmod lbmethod_byrequests
~~~
#### Copiamos el archivo de configuración 
~~~
cp ../conf/load-balancer.conf /etc/apache2/sites-available
~~~
#### Reemplazamos los valores de la plantilla por las direcciones ip de los dos frontales
~~~
sed -i "s/IP_HTTP_SERVER_1/$IP_HTTP_SERVER_2/" /etc/apache2/sites-available/load-balancer.conf
sed -i "s/IP_HTTP_SERVER_2/$IP_HTTP_SERVER_1/" /etc/apache2/sites-available/load-balancer.conf
~~~
#### Habilitamos el VirtualHost que hemos creado 
~~~
a2ensite load-balancer.conf 
~~~
#### Deshabilitamos el VirtualHost que tiene Apache por defecto
~~~
a2dissite 000-default.conf
~~~
#### Reiniciamos el servicio de apache
~~~
systemctl restart apache2
~~~ 
