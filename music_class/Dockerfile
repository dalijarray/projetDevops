FROM python:3.12-slim

WORKDIR /app

# Installer les dépendances système nécessaires
RUN python -m pip install --upgrade pip

COPY requirements.txt /app/

# Installer pip et les dépendances Python
RUN python -m pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

COPY Trained_model.h5 /app/

COPY app.py /app/

EXPOSE 5000

CMD ["python", "app.py"]
