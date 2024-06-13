FROM node:18-alpine AS development
WORKDIR /nestjs_core
COPY package*.json ./
RUN npm install
RUN npm install prisma --save-dev
COPY . .
RUN npx prisma generate
RUN npm run build


FROM node:18-alpine AS production
WORKDIR /nestjs_core
COPY package*.json ./
RUN npm install --only=production
COPY --from=development /nestjs_core/node_modules/.prisma ./node_modules/.prisma
COPY --from=development /nestjs_core/node_modules/@prisma ./node_modules/@prisma
COPY --from=development /nestjs_core/prisma ./prisma
COPY --from=development /nestjs_core/dist ./dist
EXPOSE 3000

# Run the Prisma migration and then the app
CMD ["sh", "-c", "npx prisma migrate deploy --schema=./prisma/schema.prisma && node dist/main"]
