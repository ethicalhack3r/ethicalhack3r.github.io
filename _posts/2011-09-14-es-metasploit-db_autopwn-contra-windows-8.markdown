---
layout: post
status: publish
published: true
title: "[ES] Metasploit db_autopwn contra Windows 8"
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Mi primer blog post en Español! <em>(lo siento si mi Español escrito no
  es perfecto)</em>\r\n\r\nAyer (o el anterior) Microsoft hizo disponible \"Windows
  8 Developer Preview\" para cualquier persona poder descargar. Yo hize la instalación
  en <a href=\"http://www.virtualbox.org/\" target=\"_blank\">VirtualBox</a> siguiendo
  este <a href=\"http://geekswithblogs.net/RollingIT/archive/2011/09/14/getting-hands-on-with-virtual-machine-of-windows-8.aspx\"
  target=\"_blank\">guía</a> (en Ingles).\r\n\r\nQuería ver si Microsoft posiblemente
  han usado algunas librerías/programas de versiones de Windows antiguos que posiblemente
  tengan vulnerabilidades remotos y que el <a href=\"http://metasploit.com/\" target=\"_blank\">Metesploit</a>
  tenga un exploit para el.\r\n\r\nPara esto quería usar el db_autopwn para que Metasploit
  use todos los exploits que tenga para los puertos que Windows 8 Developer tenga
  abierto. Al mismo ves será un test rápido y sencillo.\r\n\r\n<em>(Configuración
  para BT5 R1, usando Metasploit revision 13728)</em>\r\n\r\n"
wordpress_id: 16508
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16508
date: '2011-09-14 17:12:24 +0100'
date_gmt: '2011-09-14 16:12:24 +0100'
---
<p>Mi primer blog post en Español! <em>(lo siento si mi Español escrito no es perfecto)</em></p>
<p>Ayer (o el anterior) Microsoft hizo disponible "Windows 8 Developer Preview" para cualquier persona poder descargar. Yo hize la instalación en <a href="http://www.virtualbox.org/" target="_blank">VirtualBox</a> siguiendo este <a href="http://geekswithblogs.net/RollingIT/archive/2011/09/14/getting-hands-on-with-virtual-machine-of-windows-8.aspx" target="_blank">guía</a> (en Ingles).</p>
<p>Quería ver si Microsoft posiblemente han usado algunas librerías/programas de versiones de Windows antiguos que posiblemente tengan vulnerabilidades remotos y que el <a href="http://metasploit.com/" target="_blank">Metesploit</a> tenga un exploit para el.</p>
<p>Para esto quería usar el db_autopwn para que Metasploit use todos los exploits que tenga para los puertos que Windows 8 Developer tenga abierto. Al mismo ves será un test rápido y sencillo.</p>
<p><em>(Configuración para BT5 R1, usando Metasploit revision 13728)</em></p>
<p><a id="more"></a><a id="more-16508"></a></p>
<p><strong>Preparando MySQL</strong></p>
<p>Instalar el Ruby gem 'mysql':</p>
<blockquote><p>gem install --user-install mysql</p></blockquote>
<p>Iniciar el MySQL servidor:</p>
<blockquote><p>service mysql start</p></blockquote>
<p>Connectar a el MySQL servidor (contraseña 'toor'):</p>
<blockquote><p>mysql -u root -p</p></blockquote>
<p>Crear un base de datos para Metasploit:</p>
<blockquote><p>create database msf;</p></blockquote>
<p>Ahora puedes salir de el cliente MySQL:</p>
<blockquote><p>exit</p></blockquote>
<p><strong>Preparar Metasploit</strong></p>
<p>Inicia a el Metasploit Consola (msfconsole):</p>
<blockquote><p>/pentest/exploits/framework/msfconsole</p></blockquote>
<p>Configuramos a Metaploit para usar el driver MySQL:</p>
<blockquote><p>db_driver mysql</p></blockquote>
<p>Connecta al base de datos 'msf':</p>
<blockquote><p>db_connect root:toor@localhost/msf</p></blockquote>
<p>Averigua si estamos connectado:</p>
<blockquote><p>db_status</p></blockquote>
<p>Hacer un scan de nmap contra el sistema Windows 8. Los resultados se guardan automáticamente en el base de datos msf:<br />
<em>(puertos abiertos 135,139,445,554,2869,5357,10243)</em></p>
<blockquote><p>db_nmap -Pn 192.168.1.115</p></blockquote>
<p>Finalmente, ejecutar db_autopwn!</p>
<blockquote><p>db_autopwn -p -t -e</p></blockquote>
<p>Los resultados?!</p>
<blockquote><p>[*] The autopwn command has completed with 0 sessions</p></blockquote>
<p>Pero bueno, pensé que valía la pena hacer el intento. :)</p>
