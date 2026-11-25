FROM node:20-bookworm-slim

# wget n'est pas présent dans l'image de base
RUN apt-get update && apt-get install -y wget

WORKDIR /opt

# 1. Télécharger la dernière version de Wiki.js
RUN wget https://github.com/Requarks/wiki-v2/releases/latest/download/wiki-js.tar.gz

# 2. Extraire le paquet
RUN mkdir wiki
RUN tar xzf wiki-js.tar.gz -C ./wiki

WORKDIR /opt/wiki

# 3. Renommer le fichier de configuration d'exemple
RUN mv config.sample.yml config.yml

# 4. La configuration réelle est injectée par montage du config.yml

EXPOSE 3000

# 6. Lancer Wiki.js
CMD ["node", "server"]
