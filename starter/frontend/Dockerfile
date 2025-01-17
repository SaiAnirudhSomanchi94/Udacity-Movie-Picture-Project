FROM  public.ecr.aws/docker/library/node:18.14.2-alpine3.17

ARG REACT_APP_MOVIE_API_URL
ENV REACT_APP_MOVIE_API_URL=${REACT_APP_MOVIE_API_URL}

WORKDIR /app

# Copy dependdency files
COPY starter/frontend/package.json ./
COPY starter/frontend/package-lock.json ./

## Check PATH
RUN pwd

# Check files
RUN ls

# Install packages
RUN npm ci ./package-lock.json

# Copy code
RUN mkdir public
COPY starter/frontend/public/* ./public/

RUN mkdir src
COPY starter/frontend/src/* ./src/

RUN mkdir src/components
COPY starter/frontend/src/components/* ./src/components/

RUN mkdir src/components/__tests__
COPY starter/frontend/src/components/__tests__/* ./src/components/__tests__/

RUN ls
# RUN cp starter/frontend/public/* /app/public/*

# Build the app
RUN npm run build



# Expose the port used by the React app
EXPOSE 3000
EXPOSE 8080

# Start the React app when the container starts
CMD ["npm", "run", "serve"]