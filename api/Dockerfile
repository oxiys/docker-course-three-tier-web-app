FROM python:3.11-slim

WORKDIR /api

# 1. Creazione di un utente e gruppo non-root
RUN addgroup --system appgroup && adduser --system --ingroup appgroup appuser

# Installazione dei pacchetti di sistema con --no-install-recommends
RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends gcc default-libmysqlclient-dev pkg-config \
    && rm -rf /var/lib/apt/lists/*

# Copia delle dipendenze Python
COPY requirements.txt ./

RUN pip install --upgrade pip setuptools wheel>=0.46.2 jaraco.context>=6.1.0
RUN pip install --no-cache-dir -r requirements.txt

# Copia del codice sorgente
COPY . .

# Assegnazione dei permessi della cartella di lavoro all'utente non-root
RUN chown -R appuser:appgroup /api

# 2. Impostazione dell'utente non-root per l'esecuzione del container
USER appuser

EXPOSE 5001

CMD ["python", "api.py"]
