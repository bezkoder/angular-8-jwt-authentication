# Angular 8 JWT Authentication example

## Flow for User Registration and User Login
For JWT – Token based Authentication with Web API, we’re gonna call 2 endpoints:
- POST `api/auth/signup` for User Registration
- POST `api/auth/signin` for User Login

You can take a look at following flow to have an overview of Requests and Responses that Angular 10 Client will make or receive.

![angular-8-jwt-authentication-flow](angular-8-jwt-authentication-flow.png)

## Angular JWT App Diagram with Router and HttpInterceptor
![angular-8-jwt-authentication-overview](angular-8-jwt-authentication-overview.png)

For more detail, please visit:
> [Angular 8 JWT Authentication with Web API](https://bezkoder.com/angular-jwt-authentication/)

> [Angular 10 JWT Authentication with Web API](https://bezkoder.com/angular-10-jwt-auth/)

## With Spring Boot back-end

> [Angular 8 + Spring Boot: JWT Authentication & Authorization example](https://bezkoder.com/angular-spring-boot-jwt-auth/)

> [Angular 10 + Spring Boot: JWT Authentication & Authorization example](https://bezkoder.com/angular-10-spring-boot-jwt-auth/)

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`.

## With Node.js Express back-end

> [Node.js Express + Angular 8: JWT Authentication & Authorization example](https://bezkoder.com/node-js-express-angular-jwt-auth/)

> [Node.js Express + Angular 10: JWT Authentication & Authorization example](https://bezkoder.com/node-js-express-angular-10-jwt-auth/)

Open `app/_helpers/auth.interceptor.js`, modify the code to work with **x-access-token** like this:
```js
...

// const TOKEN_HEADER_KEY = 'Authorization'; // for Spring Boot back-end
const TOKEN_HEADER_KEY = 'x-access-token';   // for Node.js Express back-end

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  ...

  intercept(req: HttpRequest<any>, next: HttpHandler) {
    ...
    if (token != null) {
      // for Spring Boot back-end
      // authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, 'Bearer ' + token) });

      // for Node.js Express back-end
      authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, token) });
    }
    return next.handle(authReq);
  }
}

...
```

Run `ng serve --port 8081` for a dev server. Navigate to `http://localhost:8081/`.

## More Practice

> [Angular 8 CRUD application example with Web API](https://bezkoder.com/angular-crud-app/)

> [Angular 8 Pagination example | ngx-pagination](https://bezkoder.com/ngx-pagination-angular-8/)

> [Angular 8 Multiple Files upload example](https://bezkoder.com/angular-multiple-files-upload/)

Fullstack with Node.js Express:
> [Angular 8 + Node.js Express + MySQL](https://bezkoder.com/angular-node-express-mysql/)

> [Angular 8 + Node.js Express + PostgreSQL](https://bezkoder.com/angular-node-express-postgresql/)

> [Angular 8 + Node.js Express + MongoDB](https://bezkoder.com/angular-mongodb-node-express/)

Fullstack with Spring Boot:
> [Angular 8 + Spring Boot + MySQL](https://bezkoder.com/angular-spring-boot-crud/)

> [Angular 8 + Spring Boot + PostgreSQL](https://bezkoder.com/angular-spring-boot-postgresql/)

> [Angular 8 + Spring Boot + MongoDB](https://bezkoder.com/angular-spring-boot-mongodb/)

Fullstack with Django:
> [Angular 8 + Django Rest Framework](https://bezkoder.com/django-angular-crud-rest-framework/)