FROM debian
MAINTAINER Sokren
# Updating Container and download pre requisites
RUN dpkg --add-architecture i386 ; apt-get update ; apt-get install -y curl lib32gcc1 libstdc++6 libstdc++6:i386 screen
# Create user and directories
RUN useradd steam ; mkdir /opt/steam/ ;  mkdir /opt/steam/steamcmd ; chown -R steam /opt/steam
# Connect to the user created and download steamcmd
RUN su - steam ; 
WORKDIR /opt/steam/steamcmd
RUN curl -s http://media.steampowered.com/installer/steamcmd_linux.tar.gz | tar -vxz
# Update and install Steam & CS GO
RUN /opt/steam/steamcmd/steamcmd.sh +login anonymous +force_install_dir ./csgo/ +app_update 740 validate +quit

# Auto connect to steamcmd 
#ENTRYPOINT ["/opt/steam/steamcmd/steamcmd.sh"]
ENTRYPOINT ["/opt/steam/steamcmd/csgo/srcds_run"]
CMD ["+maxplayers", "16", "+map", "de_dust2"]
# Expose the port to connect to the server
EXPOSE 27015/udp
