
1. First thing first, we need to have docker installed in our system, this steps are
made for an ubuntu based OS (all of it, not only for docker).
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04-es

2. With docker installed, we need to pull a dgraph image from the hub, there is a standalone image used for testing and to get started the command below will pull and run the image in a container:

docker run -it -p 8080:8080 dgraph/standalone:v20.03.0

And a production ready image, the command below will only download the image:

docker pull dgraph/dgraph:latest

3. Dgraph is a graph database implementing GraphQL natively, so we need to load an schema, the command below will load an schema, you need to paste it in the therminal (you need to have curl installed):

curl -H "Content-Type: application/json" http://localhost:8080/admin/schema -XPOST -d $'
type City{
 id: ID!
 lat: Float!
 lng: Float!
 name: String! @search(by:[exact])
}'

