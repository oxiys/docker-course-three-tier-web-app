FROM python:3.11-slim

WORKDIR /app

# 1. Creazione di un utente e gruppo non-root
RUN addgroup --system appgroup && adduser --system --ingroup appgroup appuser

COPY . /app

# Upgrade dei tool di build e installazione dipendenze
RUN pip install --upgrade pip setuptools wheel>=0.46.2 jaraco.context>=6.1.0
RUN pip install --no-cache-dir -r requirements.txt

# Assegnazione dei permessi della cartella /app all'utente non-root
RUN chown -R appuser:appgroup /app

# 2. Impostazione dell'utente non-root per l'esecuzione
USER appuser

EXPOSE 5002

# 5002 this is for local dev

CMD ["python", "app.py"]
