1.- crear un cluster
2.- crear 2 nodo
	hdd 40 + hdd 100 + 1core
3.- Crear grupo de seguridad
	80 - 22 - icmp - 
3.- configuracion del nodo
	agregar grupo de seguridad
	docker --version
4.- subir imagenes
	crear directorio docker
		mkdir -p ~/.docker
		cd ~/.docker
		vim config.json
	bajar credenciales del docker
	editar archivo del servicio docker
		vim /usr/lib/systemd/system/docker.service
	buscar la linea ExecStart= y al final agregar
		--insecure-registry ip:443
	autenticar docker
		echo -n llave | base64 -d
	Loguear en docker
		docker login -u _auth_token -p passwordllave -e aa 200.29.32.137:443
5.- contruir nuestro contenedor 
	mkdir guestbook
	cd guestbook
	mkdir frontend
	cd frontend
	vim guestbook.php
	vim controoler.js
	vim index.html
	vim Dockerfile
	docker build -t frontend .
	docker pull redis:3.0
	cd ..
	mkdir Redis_slave
	cd Redis_slave
	vim run.sh
	vim Dockerfile
	docker build -t redisslave .
	docker images
6.- subir los contenedores (docker tag images_id 172.20.124.81:443/username/image_name:version)
	docker tag
	docker push
7.- crear el componente https://support.telefonicaopencloud.com/en-us/usermanual/cce/en-us_topic_0035200306.html