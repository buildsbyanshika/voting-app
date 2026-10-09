FROM node:20-alpine

WORKDIR /app
ENV NODE_ENV=production PORT=8000

COPY package*.json ./
RUN npm ci --omit=dev && npm cache clean --force

COPY . .
EXPOSE 8000

CMD ["node", "server.js"]