FROM mysql:latest

# Configurazione del nome del database (variabile non sensibile)
ENV MYSQL_DATABASE=quotesdb

# Copia dello script SQL assegnando la proprietà all'utente mysql
COPY --chown=mysql:mysql init.sql /docker-entrypoint-initdb.d/

# Impostazione dell'utente non-root fornito dall'immagine ufficiale MySQL
USER mysql
