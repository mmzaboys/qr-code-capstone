FROM node:18-alpine as base
WORKDIR /app
COPY package.json yarn.lock* package-lock.json* pnpm-lock.yaml* ./ 
RUN if [ -f yarn.lock ]; then yarn install; \
    elif [ -f package-lock.json ]; then npm install; \
    elif [ -f pnpm-lock.yaml ]; then pnpm install; \
    else echo "No lock file found"; fi
COPY    . .
RUN npm run build
EXPOSE  3000
CMD ["npm", "start"]