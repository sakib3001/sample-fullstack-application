# Stage - 1
FROM node:22-alpine AS builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
ENV NEXT_PUBLIC_BACKEND_BASE_URL=http://localhost:8777
RUN npm run build

# Stage - 2
FROM node:alpine AS runner
WORKDIR /app
COPY --from=builder /app/.next ./.next
COPY --from=builder /app/public ./public
COPY --from=builder /app/package.json ./
COPY --from=builder /app/next.config.mjs ./
RUN npm install --production

EXPOSE 3000

CMD ["npm","start"]