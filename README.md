# Spring reCAPTCHA

Este é um módulo de segurança que encapsula a lógica de válidação de reCAPTCHA 
para aplicações Spring Boot. No momento funciona apenas para reCAPTCHAv2.

## Como usar

Adicione ao seu pom a seguinte dependência:

```
<dependency>
  <groupId>com.github.jovanibrasil</groupId>
  <artifactId>recaptcha-sec-module</artifactId>
  <version>1.0.0</version>
</dependency>
```
Então você deve adicionar as chaves site e secret ao seu ```application.properties```:

```
captcha.keysite=${YOUR_RECAPTCHA_KEY_SITE}
captcha.keysecret=${YOUR_RECAPTCHA_KEY_SECRET}
```

Por fim você deve habilitar o módulo nas suas configurações utilizando a anotação 
```@EnableRecaptchaVerification``` e em cada método que for necessário a validação
você adiciona a anotação @Recaptcha. Por exemplo:

```
@Configuration
@EnableWebSecurity
@EnableRecaptchaVerification
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {
...
}
```
```
@Recaptcha
@PutMapping
public ResponseEntity<UserDTO> updateUser(@Valid @RequestBody UpdateUserForm userDto){ 
  ... 
}
```
E é isso. Qualquer dúvida entre em contato.







