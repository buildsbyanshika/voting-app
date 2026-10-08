FROM node:20-slim

WORKDIR /app
ENV NODE_ENV=production PORT=8000

COPY package*.json ./
RUN npm ci --omit=dev  || npm install --omit=dev

COPY . .
EXPOSE 8000

CMD ["node", "server.js"]