#................ single stage dockerfile.................

# FROM node
# RUN apt update && apt install -y nodejs npm
# WORKDIR /elearnApp
# COPY . .
# RUN npm install
# RUN npm run build
# RUN apt update
# RUN apt install -y nginx
# RUN cp -r /elearnApp/build/* /var/www/html/
# CMD nginx -g "daemon off;"d

# .........................for multi-stage dockerfile........................... 

FROM node as build  
# bana banya image ko build karne ke liye node ka use kiya hai 
# is image me node install hai isliye humne npm install karne ke liye node ka use kiya hai
WORKDIR /elearnapp
#  elearnapp ke liye ek directory banayi hai
COPY package.json .
# COPY package.json file ko copy kiya hai
RUN npm install
COPY . .
RUN npm run build
FROM nginx
#NYA IMAGE BANANE KE LIYE NGINX KA USE KIYA HAI
COPY --from=build /elearnapp/build /usr/share/nginx/html
# COPY use ktrke build stage se build folder ko nginx ke html folder me copy kiya hai.