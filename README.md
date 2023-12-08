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
