# Assignment

Your task is to setup a simple Symfony <https://symfony.com> project authenticating users against a Keycloak <https://www.keycloak.org> server with an OpenID Connect protocol client.

* Implement a custom stateless authenticator in Symfony,
* which reads a JWT access token generated by Keycloak from the Request authorization header,
* decodes and validates it with the PHP-JWT library <https://github.com/firebase/php-jwt> using a JWK accessible via Keycloak's OpenID certificate endpoint <https://www.keycloak.org/docs/latest/securing_apps/#_certificate_endpoint>
* and authenticates the user using the `SelfValidatingPassport` <https://symfony.com/doc/current/security/custom_authenticator.html#self-validating-passport>.
* Write a functional test testing authentication success and failure.

To help you get started there's a Docker Compose setup running a pre-configured Keycloak server and here is an example on how to generate a JWT access token against it:

```
curl -XPOST 'http://localhost:8080/realms/myrealm/protocol/openid-connect/token' \
  -d 'client_id=test-client-id' -d 'username=john.doe@example.com' -d 'password=password' -d 'grant_type=password' \
  | jq

```

Good Luck!
