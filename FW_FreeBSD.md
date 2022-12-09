# Configuracion

 Configuraos las reglas del FW con la configuracion indicada abajo en el fichero /etc/rc.firewall

<pre>
#!/bin/sh
################ Start of IPFW rules file ###############################
# Flush out the list before we begin.
ipfw -q -f flush

# Set rules command prefix
cmd="ipfw -q add"
skip="skipto 800"
# pif="rl0"     # public interface name of NIC
              # facing the public Internet

#################################################################
# No restrictions on Inside LAN Interface for private network
# Change xl0 to your LAN NIC interface name
#################################################################
$cmd 005 allow all from any to any via vmx0
</pre>
con esta configuracion estamos permitiendo todo el trafico.

# Habilitamos el servcio

 sysrc firewall_enable="YES"

# Arrancamos FW

  service ipfw start

# Checkeos

Para comprobar las ips bloqueadas ejecutamos


ipfw table all list

![image](https://user-images.githubusercontent.com/42178316/206706681-3d638239-f67c-4a37-92f9-2e3d08aba4be.png)
