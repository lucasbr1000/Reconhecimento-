# Use uma imagem base oficial do Python
FROM python:3.11-slim

# Defina o diretório de trabalho
WORKDIR /app

# Instale TODAS as dependências de sistema necessárias para o OpenCV
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender-dev \
    && rm -rf /var/lib/apt/lists/*

# Copie e instale as dependências do Python
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copie o resto do seu aplicativo
COPY . .

# Exponha a porta
EXPOSE 5000

# Comando para iniciar o aplicativo
CMD ["gunicorn", "main:app", "--bind", "0.0.0.0:5000"]

