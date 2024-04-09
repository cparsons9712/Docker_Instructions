# Check node version with which node and use it here
FROM node:18

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

ENV PORT=8000

EXPOSE 8000
# Copy the entrypoint script
COPY entrypoint.sh /usr/src/app/entrypoint.sh
# Make the script executable (optional if you've already made it executable on the host)
RUN chmod +x /usr/src/app/entrypoint.sh
# Set the script as the entrypoint
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]

CMD ["npm", "run", "start:dev"]
