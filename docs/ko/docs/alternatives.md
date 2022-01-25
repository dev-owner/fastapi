# 대안, 영감 그리고 비교들

**FastAPI**에 영감을 준 것들, 다른 대안들과 비교하고 그것들로부터 무엇을 배웠는지에 대하여 말하고자 합니다.

## 들어가며

**FastAPI**은 다른 사람들의 이전 작업이 없었다면 존재할 수 없었을 것입니다.

FastAPI의 탄생에 도움을 준 수많은 도구들이 있습니다.

지난 몇년간 저는 새로운 프레임워크를 만드는 것을 피해 왔습니다. 우선 FastAPI에 있는 모든 기능들을 많은 다른 프레임워크나 플러그인, 그리고 도구들로 해결하려고 노력했었습니다.

그러나 어느 시점에서, 이전에 없었던 언어의 기능들(Python 3.6+ type hints)을 사용하며 이전 도구들로부터 최고의 아이디어를 가져오고 가능한 최고의 방법들로 기능들을 조합해서 모든 기능들을 제공하는 무언가를 만드는 것 말고 다른 대안이 없었습니다.  

## 과거의 도구들

### <a href="https://www.djangoproject.com/" class="external-link" target="_blank">Django</a>

파이썬 프레임워크 중 가장 유명하며, 광범위하게 신뢰받고 있습니다. 인스타그램같은 시스템을 만들 때 사용되었습니다.

관계형 데이터베이스(MySQL이나 PostgreSQL)와 상대적으로 강력하게 결합되어 있어서, NoSQL 데이터베이스(Couchbase, MongoDB, Cassandra, etc)를 주 저장 엔진으로 사용하기는 매우 어렵습니다.

현대 프론트엔드(React, Vue.js, Angular)나 다른 시스템들(<abbr title="Internet of Things">IoT</abbr> 장치들)과 통신하기 위한 API를 생성하지는 않고, backend에서 HTML을 생성하기 위해 만들어졌습니다. 


### <a href="https://www.django-rest-framework.org/" class="external-link" target="_blank">Django REST Framework</a>

Django REST 프레임워크는 Django의 API 기능을 향상시키기 위해, Django에서 사용하기 위한 Web API를 만들기 위한 유연한 도구로써 제작되었습니다. 

Django는 Mozilla, Red Hat 그리고 Eventbrite과 같은 여러 회사에서 사용되고 있습니다.

이것은 **자동 API 문서화**의 첫번째 예시 중 하나이고, **FastAPI**의 검색기능이 특별히 영감을 받았던 첫번째 아이디어 중 하나입니다.

!!! note
    Django REST 프레임워크는 Tom Christie가 만들었습니다. **FastAPI**의 근간이 된 Starlette and Uvicorn의 제작자와 동일 인물입니다. 

!!! check "**FastAPI**에 영감을 준 것"
    자동 API 문서 사용자 유저 인터페이스
    

### <a href="https://flask.palletsprojects.com" class="external-link" target="_blank">Flask</a>

Flask는 "마이크로 프레임워크"입니다. 데이터베이스 통합이 없을 뿐더러, Django에서 제공하는 기본적인 많은것들도 포함하고 있지 않습니다.

이러한 단순함과 유연성은 NoSQL 데이터베이스를 주 데이터 저장소 시스템으로 사용하는것과 같은 많은 것을 허용합니다.

Flask는 매우 간단하기 때문에, 문서가 어느 부분에서는 다소 기술적으로 설명되긴 하지만 상대적으로 학습하기에 직관적입니다.

데이터베이스나 유저 관리나, Django에서 기본적으로 제공하는 수많은 기능들이 필요하지 않은 많은 다른 애플리케이션에서 Flask가 보통 사용되곤 합니다. 그리고 필요한 수많은 기능들은 플러그인으로 대부분 추가할수도 있습니다. 

이러한 영역들의 분리와 필요한 것을 정확히 포함하도록 확장할 수 있는 "마이크로 프레임워크"화 하는것은 제가 유지하고 싶었던 핵심 기능입니다.

Flask의 단숨함으로, API를 만드는 것은 적합해 보입니다. 그 다음으로 찾은 것은 Flask용 "Django REST 프레임워크"였습니다.

!!! check "**FastAPI**에 영감을 준 것"
    마이크로 프레임워크가 되는 것. 필요한 부품과 도구를 쉽게 합칠 수 있게 하는 것. 

    단순하게 하고 라우팅 시스템을 사용하기 쉽게 하는 것. 


### <a href="https://requests.readthedocs.io" class="external-link" target="_blank">Requests</a>

**FastAPI**는 사실 **Requests**의 대안은 아닙니다. 그것들이 다루는 범위는 아주 다릅니다.

Requests는 사실 FastAPI 애플리케이션 *안*에서 보통 사용됩니다.

그러나 여전히, FastAPI는 Requests로부터 어느정도 영감을 받았습니다.

**Requests**는 API(클라이언트로써) 로 상호 작용 하기 위한 라이브러리인 반면에, **FastAPI**는 API(서버로써)를 *만들기* 위한 라이브러리입니다.

위 두가지는 양 극단에서 서로를 상호 보완합니다.

Requests는 매우 간단하고 직관적인 디자인을 가지고 있고 합리적인 기본값으로 매우 사용하기 쉬울 뿐더러, 동시에 매우 강력하고 변경이 쉽습니다.

그것이 공식 웹 사이트에서 아래와 같이 말하는 이유입니다:

> Requests는 가장 많은 다운로드를 가지고 있는 파이썬 패키지입니다.

그것을 사용하는 방법은 매우 간단합니다. 예를들어, `GET` 요청을 하기 위해, 아래와 같이 작성하면 됩니다.

```Python
response = requests.get("http://example.com/some/url")
```

이에 상응하는 FastAPI의 *경로 작업*은 아래와 같습니다:

```Python hl_lines="1"
@app.get("/some/url")
def read_url():
    return {"message": "Hello World"}
```

`requests.get(...)` 와 `@app.get(...)`의 유사함을 보십시오.


!!! check "**FastAPI**에 영감을 준 것"
    * 간단하고 직관적인 API
    * 간단하고 직관적인 방법으로 HTTP method 이름(동작들)을 직접 사용
    * 합리적인 기본값을 가지면서 변경에 매우 강력한 점


### <a href="https://swagger.io/" class="external-link" target="_blank">Swagger</a> / <a href="https://github.com/OAI/OpenAPI-Specification/" class="external-link" target="_blank">OpenAPI</a>

제가 Django REST Framework에서 원한 주요 기능은 자동 API 문서화 기능입니다.

그리고 Swagger라고 불리는, JSON(혹은 YAML, JSON의 확장판)을 사용하는 API를 문서화 하기 위한 표준을 찾았습니다. 

그리고 Swagger APIs를 위한 웹 유저 인터페이스가 이미 생성되어 있었습니다. 그러므로, API에 대한 Swagger 문서를 생성할 수 있다면, 이러한 웹 유저 인터페이스를 자동으로 사용할 수 있습니다.

어느 시점에서, Swagger는 OpenAPI로 이름이 바뀌며 리눅스 재단에 기증되었습니다.

그것이 2.0 버전에서는 보통 "Swagger"라고 부르고, 3+ 버전에서는 "OpenAPI"로 부르는 이유입니다.

!!! check "**FastAPI**에 영감을 준 것"
    API 사양에 사용자 지정 스키마 대신 공개 표준을 사용하고 적용한 것

    그리고 표준기반 사용자 인터페이스 도구를 통합한 것:

    * <a href="https://github.com/swagger-api/swagger-ui" class="external-link" target="_blank">Swagger UI</a>
    * <a href="https://github.com/Rebilly/ReDoc" class="external-link" target="_blank">ReDoc</a>

    이 두가지는 유명하고 안정적인 기준으로 선택되었지만, 깊이 조사하지 못한 탓에 OpenAPI에 대한 사용자 인터페이스 대안(당신이 **FastAPI**와 함꼐 사용할)을 훨씬 더 많이 찾을 수도 있습니다.

### Flask REST frameworks

There are several Flask REST frameworks, but after investing the time and work into investigating them, I found that many are discontinued or abandoned, with several standing issues that made them unfit.

### <a href="https://marshmallow.readthedocs.io/en/3.0/" class="external-link" target="_blank">Marshmallow</a>

One of the main features needed by API systems is data "<abbr title="also called marshalling, conversion">serialization</abbr>" which is taking data from the code (Python) and converting it into something that can be sent through the network. For example, converting an object containing data from a database into a JSON object. Converting `datetime` objects into strings, etc.

Another big feature needed by APIs is data validation, making sure that the data is valid, given certain parameters. For example, that some field is an `int`, and not some random string. This is especially useful for incoming data.

Without a data validation system, you would have to do all the checks by hand, in code.

These features are what Marshmallow was built to provide. It is a great library, and I have used it a lot before.

But it was created before there existed Python type hints. So, to define every <abbr title="the definition of how data should be formed">schema</abbr> you need to use specific utils and classes provided by Marshmallow.

!!! check "Inspired **FastAPI** to"
    Use code to define "schemas" that provide data types and validation, automatically.

### <a href="https://webargs.readthedocs.io/en/latest/" class="external-link" target="_blank">Webargs</a>

Another big feature required by APIs is <abbr title="reading and converting to Python data">parsing</abbr> data from incoming requests.

Webargs is a tool that was made to provide that on top of several frameworks, including Flask.

It uses Marshmallow underneath to do the data validation. And it was created by the same developers.

It's a great tool and I have used it a lot too, before having **FastAPI**.

!!! info
    Webargs was created by the same Marshmallow developers.

!!! check "Inspired **FastAPI** to"
    Have automatic validation of incoming request data.

### <a href="https://apispec.readthedocs.io/en/stable/" class="external-link" target="_blank">APISpec</a>

Marshmallow and Webargs provide validation, parsing and serialization as plug-ins.

But documentation is still missing. Then APISpec was created.

It is a plug-in for many frameworks (and there's a plug-in for Starlette too).

The way it works is that you write the definition of the schema using YAML format inside the docstring of each function handling a route.

And it generates OpenAPI schemas.

That's how it works in Flask, Starlette, Responder, etc.

But then, we have again the problem of having a micro-syntax, inside of a Python string (a big YAML).

The editor can't help much with that. And if we modify parameters or Marshmallow schemas and forget to also modify that YAML docstring, the generated schema would be obsolete.

!!! info
    APISpec was created by the same Marshmallow developers.


!!! check "Inspired **FastAPI** to"
    Support the open standard for APIs, OpenAPI.

### <a href="https://flask-apispec.readthedocs.io/en/latest/" class="external-link" target="_blank">Flask-apispec</a>

It's a Flask plug-in, that ties together Webargs, Marshmallow and APISpec.

It uses the information from Webargs and Marshmallow to automatically generate OpenAPI schemas, using APISpec.

It's a great tool, very under-rated. It should be way more popular than many Flask plug-ins out there. It might be due to its documentation being too concise and abstract.

This solved having to write YAML (another syntax) inside of Python docstrings.

This combination of Flask, Flask-apispec with Marshmallow and Webargs was my favorite backend stack until building **FastAPI**.

Using it led to the creation of several Flask full-stack generators. These are the main stack I (and several external teams) have been using up to now:

* <a href="https://github.com/tiangolo/full-stack" class="external-link" target="_blank">https://github.com/tiangolo/full-stack</a>
* <a href="https://github.com/tiangolo/full-stack-flask-couchbase" class="external-link" target="_blank">https://github.com/tiangolo/full-stack-flask-couchbase</a>
* <a href="https://github.com/tiangolo/full-stack-flask-couchdb" class="external-link" target="_blank">https://github.com/tiangolo/full-stack-flask-couchdb</a>

And these same full-stack generators were the base of the [**FastAPI** Project Generators](project-generation.md){.internal-link target=_blank}.

!!! info
    Flask-apispec was created by the same Marshmallow developers.

!!! check "Inspired **FastAPI** to"
    Generate the OpenAPI schema automatically, from the same code that defines serialization and validation.

### <a href="https://nestjs.com/" class="external-link" target="_blank">NestJS</a> (and <a href="https://angular.io/" class="external-link" target="_blank">Angular</a>)

This isn't even Python, NestJS is a JavaScript (TypeScript) NodeJS framework inspired by Angular.

It achieves something somewhat similar to what can be done with Flask-apispec.

It has an integrated dependency injection system, inspired by Angular two. It requires pre-registering the "injectables" (like all the other dependency injection systems I know), so, it adds to the verbosity and code repetition.

As the parameters are described with TypeScript types (similar to Python type hints), editor support is quite good.

But as TypeScript data is not preserved after compilation to JavaScript, it cannot rely on the types to define validation, serialization and documentation at the same time. Due to this and some design decisions, to get validation, serialization and automatic schema generation, it's needed to add decorators in many places. So, it becomes quite verbose.

It can't handle nested models very well. So, if the JSON body in the request is a JSON object that has inner fields that in turn are nested JSON objects, it cannot be properly documented and validated.

!!! check "Inspired **FastAPI** to"
    Use Python types to have great editor support.

    Have a powerful dependency injection system. Find a way to minimize code repetition.

### <a href="https://sanic.readthedocs.io/en/latest/" class="external-link" target="_blank">Sanic</a>

It was one of the first extremely fast Python frameworks based on `asyncio`. It was made to be very similar to Flask.

!!! note "Technical Details"
    It used <a href="https://github.com/MagicStack/uvloop" class="external-link" target="_blank">`uvloop`</a> instead of the default Python `asyncio` loop. That's what made it so fast.

    It clearly inspired Uvicorn and Starlette, that are currently faster than Sanic in open benchmarks.

!!! check "Inspired **FastAPI** to"
    Find a way to have a crazy performance.
    
    That's why **FastAPI** is based on Starlette, as it is the fastest framework available (tested by third-party benchmarks).

### <a href="https://falconframework.org/" class="external-link" target="_blank">Falcon</a>

Falcon is another high performance Python framework, it is designed to be minimal, and work as the foundation of other frameworks like Hug.

It is designed to have functions that receive two parameters, one "request" and one "response". Then you "read" parts from the request, and "write" parts to the response. Because of this design, it is not possible to declare request parameters and bodies with standard Python type hints as function parameters.

So, data validation, serialization, and documentation, have to be done in code, not automatically. Or they have to be implemented as a framework on top of Falcon, like Hug. This same distinction happens in other frameworks that are inspired by Falcon's design, of having one request object and one response object as parameters.

!!! check "Inspired **FastAPI** to"
    Find ways to get great performance.

    Along with Hug (as Hug is based on Falcon) inspired **FastAPI** to declare a `response` parameter in functions.

    Although in FastAPI it's optional, and is used mainly to set headers, cookies, and alternative status codes.

### <a href="https://moltenframework.com/" class="external-link" target="_blank">Molten</a>

I discovered Molten in the first stages of building **FastAPI**. And it has quite similar ideas:

* Based on Python type hints.
* Validation and documentation from these types.
* Dependency Injection system.

It doesn't use a data validation, serialization and documentation third-party library like Pydantic, it has its own. So, these data type definitions would not be reusable as easily.

It requires a little bit more verbose configurations. And as it is based on WSGI (instead of ASGI), it is not designed to take advantage of the high-performance provided by tools like Uvicorn, Starlette and Sanic.

The dependency injection system requires pre-registration of the dependencies and the dependencies are solved based on the declared types. So, it's not possible to declare more than one "component" that provides a certain type.

Routes are declared in a single place, using functions declared in other places (instead of using decorators that can be placed right on top of the function that handles the endpoint). This is closer to how Django does it than to how Flask (and Starlette) does it. It separates in the code things that are relatively tightly coupled.

!!! check "Inspired **FastAPI** to"
    Define extra validations for data types using the "default" value of model attributes. This improves editor support, and it was not available in Pydantic before.

    This actually inspired updating parts of Pydantic, to support the same validation declaration style (all this functionality is now already available in Pydantic).

### <a href="https://www.hug.rest/" class="external-link" target="_blank">Hug</a>

Hug was one of the first frameworks to implement the declaration of API parameter types using Python type hints. This was a great idea that inspired other tools to do the same.

It used custom types in its declarations instead of standard Python types, but it was still a huge step forward.

It also was one of the first frameworks to generate a custom schema declaring the whole API in JSON.

It was not based on a standard like OpenAPI and JSON Schema. So it wouldn't be straightforward to integrate it with other tools, like Swagger UI. But again, it was a very innovative idea.

It has an interesting, uncommon feature: using the same framework, it's possible to create APIs and also CLIs.

As it is based on the previous standard for synchronous Python web frameworks (WSGI), it can't handle Websockets and other things, although it still has high performance too.

!!! info
    Hug was created by Timothy Crosley, the same creator of <a href="https://github.com/timothycrosley/isort" class="external-link" target="_blank">`isort`</a>, a great tool to automatically sort imports in Python files.

!!! check "Ideas inspired in **FastAPI**"
    Hug inspired parts of APIStar, and was one of the tools I found most promising, alongside APIStar.

    Hug helped inspiring **FastAPI** to use Python type hints to declare parameters, and to generate a schema defining the API automatically.

    Hug inspired **FastAPI** to declare a `response` parameter in functions to set headers and cookies.

### <a href="https://github.com/encode/apistar" class="external-link" target="_blank">APIStar</a> (<= 0.5)

Right before deciding to build **FastAPI** I found **APIStar** server. It had almost everything I was looking for and had a great design.

It was one of the first implementations of a framework using Python type hints to declare parameters and requests that I ever saw (before NestJS and Molten). I found it more or less at the same time as Hug. But APIStar used the OpenAPI standard.

It had automatic data validation, data serialization and OpenAPI schema generation based on the same type hints in several places.

Body schema definitions didn't use the same Python type hints like Pydantic, it was a bit more similar to Marshmallow, so, editor support wouldn't be as good, but still, APIStar was the best available option.

It had the best performance benchmarks at the time (only surpassed by Starlette).

At first, it didn't have an automatic API documentation web UI, but I knew I could add Swagger UI to it.

It had a dependency injection system. It required pre-registration of components, as other tools discussed above. But still, it was a great feature.

I was never able to use it in a full project, as it didn't have security integration, so, I couldn't replace all the features I was having with the full-stack generators based on Flask-apispec. I had in my backlog of projects to create a pull request adding that functionality.

But then, the project's focus shifted.

It was no longer an API web framework, as the creator needed to focus on Starlette.

Now APIStar is a set of tools to validate OpenAPI specifications, not a web framework.

!!! info
    APIStar was created by Tom Christie. The same guy that created:

    * Django REST Framework
    * Starlette (in which **FastAPI** is based)
    * Uvicorn (used by Starlette and **FastAPI**)

!!! check "Inspired **FastAPI** to"
    Exist.

    The idea of declaring multiple things (data validation, serialization and documentation) with the same Python types, that at the same time provided great editor support, was something I considered a brilliant idea.
    
    And after searching for a long time for a similar framework and testing many different alternatives, APIStar was the best option available.

    Then APIStar stopped to exist as a server and Starlette was created, and was a new better foundation for such a system. That was the final inspiration to build **FastAPI**.

    I consider **FastAPI** a "spiritual successor" to APIStar, while improving and increasing the features, typing system, and other parts, based on the learnings from all these previous tools.

## Used by **FastAPI**

### <a href="https://pydantic-docs.helpmanual.io/" class="external-link" target="_blank">Pydantic</a>

Pydantic is a library to define data validation, serialization and documentation (using JSON Schema) based on Python type hints.

That makes it extremely intuitive.

It is comparable to Marshmallow. Although it's faster than Marshmallow in benchmarks. And as it is based on the same Python type hints, the editor support is great.

!!! check "**FastAPI** uses it to"
    Handle all the data validation, data serialization and automatic model documentation (based on JSON Schema).

    **FastAPI** then takes that JSON Schema data and puts it in OpenAPI, apart from all the other things it does.

### <a href="https://www.starlette.io/" class="external-link" target="_blank">Starlette</a>

Starlette is a lightweight <abbr title="The new standard for building asynchronous Python web">ASGI</abbr> framework/toolkit, which is ideal for building high-performance asyncio services.

It is very simple and intuitive. It's designed to be easily extensible, and have modular components.

It has:

* Seriously impressive performance.
* WebSocket support.
* In-process background tasks.
* Startup and shutdown events.
* Test client built on requests.
* CORS, GZip, Static Files, Streaming responses.
* Session and Cookie support.
* 100% test coverage.
* 100% type annotated codebase.
* Few hard dependencies.

Starlette is currently the fastest Python framework tested. Only surpassed by Uvicorn, which is not a framework, but a server.

Starlette provides all the basic web microframework functionality.

But it doesn't provide automatic data validation, serialization or documentation.

That's one of the main things that **FastAPI** adds on top, all based on Python type hints (using Pydantic). That, plus the dependency injection system, security utilities, OpenAPI schema generation, etc.

!!! note "Technical Details"
    ASGI is a new "standard" being developed by Django core team members. It is still not a "Python standard" (a PEP), although they are in the process of doing that.

    Nevertheless, it is already being used as a "standard" by several tools. This greatly improves interoperability, as you could switch Uvicorn for any other ASGI server (like Daphne or Hypercorn), or you could add ASGI compatible tools, like `python-socketio`.

!!! check "**FastAPI** uses it to"
    Handle all the core web parts. Adding features on top.

    The class `FastAPI` itself inherits directly from the class `Starlette`.
    
    So, anything that you can do with Starlette, you can do it directly with **FastAPI**, as it is basically Starlette on steroids.

### <a href="https://www.uvicorn.org/" class="external-link" target="_blank">Uvicorn</a>

Uvicorn is a lightning-fast ASGI server, built on uvloop and httptools.

It is not a web framework, but a server. For example, it doesn't provide tools for routing by paths. That's something that a framework like Starlette (or **FastAPI**) would provide on top.

It is the recommended server for Starlette and **FastAPI**.

!!! check "**FastAPI** recommends it as"
    The main web server to run **FastAPI** applications.

    You can combine it with Gunicorn, to have an asynchronous multi-process server.

    Check more details in the [Deployment](deployment/index.md){.internal-link target=_blank} section.

## Benchmarks and speed

To understand, compare, and see the difference between Uvicorn, Starlette and FastAPI, check the section about [Benchmarks](benchmarks.md){.internal-link target=_blank}.
