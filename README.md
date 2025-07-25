# Erro da porta 80, não aparece a página do Laravel no browser do navegador.

##### Rodando o comando "sail up -d" ou "php -S localhost:8000". O erro pode ser diferente, porém a página do Laravel não mostra conteúdo, aparentando um erro de conexão, mesmo tudo no terminal não indicar erros. 
##### Porém a página do "Vite" roda no browser normalmente sem problema (com o comando "npm run dev").

#### Exemplo de erro abaixo:
> "Error response from daemon: driver failed programming external connectivity on endpoint"

**Seguir os comandos abaixo dentro do WLS2, até o final**


##### 1. O primeiro passo é parar o serviço "APACHE"
<CODE>
sudo /etc/init.d/apache2 stop
</CODE>

##### 2.
Entrar no arquivo **"ports.conf"**
<CODE>
sudo nano /etc/apache2/ports.conf
</CODE>

##### 3.
O arquivo **"ports.conf"** deve estar +- deste modo
<CODE>
###### If you just change the port or add more ports here, you will likely also
###### have to change the VirtualHost statement in
###### /etc/apache2/sites-enabled/000-default.conf
Listen 8081

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>

###### vim: syntax=apache ts=4 sw=4 sts=4 sr noet
</CODE>

#### 4.
Apenas colocar em outra porta exemplo: 8000 OU 8081 
> (ou outra parta que não esteja em uso) Comandos para gravar e sair
<CODE>
ctrl + O
ctrl + x</CODE>

### *IMPORTANTE REINICIAR O SERVIÇO
<CODE>sudo /etc/init.d/apache2 start</CODE>

