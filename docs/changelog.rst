Changelog
=========

2.0.0 (2015-06-25)
++++++++++++++++++++++
* Added ``use_models`` configuration option for Swagger 2.0 backwards compatibility with existing pyramid views

2.0.0-rc2 (2015-05-26)
++++++++++++++++++++++
* Upgraded bravado-core to 1.0.0-rc1 so basePath is used when matching a request to an operation
* Updates for refactored SwaggerError exception hierarchy in bravado-core
* Fixed file uploads that use Content-Type: multipart/form-data

2.0.0-rc1 (2015-05-13)
++++++++++++++++++++++

**Backwards Incompatible**

* Support for Swagger 2.0 - See `Migrating to Swagger 2.0`_

.. _Migrating to Swagger 2.0: http://pyramid-swagger.readthedocs.org/en/latest/migrating_to_swagger_20.html

1.5.0 (2015-05-12)
++++++++++++++++++++++

* Now using swagger_spec_validator package for spec validation. Should be far
  more robust than the previous implementation.

1.5.0-rc2 (2015-04-1)
++++++++++++++++++++++

* Form-encoded bodies are now validated correctly.
* Fixed bug in `required` swagger attribute handling.

1.5.0-rc1 (2015-03-30)
++++++++++++++++++++++

* Added ``enable_api_docs_views`` configuration option so /api-docs
  auto-registration can be disabled in situations where users want to serve
  the Swagger spec in a nonstandard way.
* Added ``exclude_routes`` configuration option. Allows a blacklist of Pyramid
  routes which will be ignored for validation purposes.
* Added ``generate_resource_listing`` configuration option to allow
  pyramid_swagger to generate the ``apis`` section of the resource listing.
* Bug fix for issues relating to ``void`` responses (See `Issue 79`_)
* Added support for header validation.
* Make casted values from the request available through
  ``request.swagger_data``

.. _Issue 79: https://github.com/striglia/pyramid_swagger/issues/79

1.4.0 (2015-01-27)
++++++++++++++++++

* Added ``validation_context_path`` setting which allows the user to specify a
  path to a contextmanager to custom handle request/response validation
  exceptions.

1.3.0 (2014-12-02)
++++++++++++++++++

* Now throws RequestValidationError and ResponseValidationError instead of
  HTTPClientError and HTTPInternalServerError respectively. The new errors
  subclass the old ones for backwards compatibility.

1.2.0 (2014-10-21)
++++++++++++++++++

* Added ``enable_request_validation`` setting which toggles whether request
  content is validated.
* Added ``enable_path_validation`` setting which toggles whether HTTP calls to
  endpoints will 400 if the URL is not described in the Swagger schema. If this
  flag is disabled and the path is not found, no validation of any kind is
  performed by pyramid-swagger.
* Added ``exclude_paths`` setting which duplicates the functionality of
  `skip_validation`. `skip_validation` is deprecated and scheduled for removal
  in the 2.0.0 release.
* Adds LICENSE file
* Fixes misuse of webtest which could cause ``make test`` to pass while
  functionality was broken.

1.1.1 (2014-08-26)
++++++++++++++++++

* Fixes bug where response bodies were not validated correctly unless they were
  a model or primitive type.
* Fixes bug where POST bodies could be mis-parsed as query arguments.
* Better backwards compatibility warnings in this changelog!

1.1.0 (2014-07-14)
++++++++++++++++++

* Swagger schema directory defaults to ``api_docs/`` rather than being a required
  configuration line.
* If the resource listing or API declarations are not at the filepaths
  expected, readable errors are raised.
* This changelog is now a part of the build documentation and backfilled to the
  initial package version.


1.0.0 (2014-07-08)
++++++++++++++++++

**Backwards Incompatible**

* Initial fully functional release.
* Your service now must supply both a resource listing and all accompanying api
  declarations.
* Swagger schemas are automatically served out of ``/api-docs`` by including the
  library.
* The api declaration basepath returned by hitting ``/api-docs/foo`` is guaranteed
  to be ``Pyramid.request.application_url``.
* Void return types are now checked.


0.5.0 (2014-07-08)
++++++++++++++++++

* Added configurable list of regular expressions to not validate
  requests/responses against.
* Vastly improved documentation! Includes a quickstart for those new to the
  library.
* Adds coverage and code health badges to README


0.4.0 (2014-06-20)
++++++++++++++++++

* Request validation now works with path arguments.
* True acceptance testing implemented for all known features. Much improved
  coverage.

0.4.0 (2014-06-20)
++++++++++++++++++

* True acceptance testing implemented for all known features. Much improved
  coverage.

0.3.2 (2014-06-16)
++++++++++++++++++

* HEAD is now an allowed HTTP method

0.3.1 (2014-06-16)
++++++++++++++++++

* Swagger spec is now validated on startup
* Fixes bug where multiple methods with the same URL were not resolved properly
* Fixes bug with validating non-string args in paths and query args
* Fixes bug with referencing models from POST bodies

0.3.0 (2014-05-29)
++++++++++++++++++

* Response validation can be disabled via configuration
* Supports Python 3.3 and 3.4!

0.2.2 (2014-05-28)
++++++++++++++++++

* Adds readthedocs links, travis badge to README
* Requests missing bodies return 400 instead of causing tracebacks

0.2.1 (2014-05-15)
++++++++++++++++++

* Requests to non-existant endpoints now return 400 errors

0.1.1 (2014-05-13)
++++++++++++++++++

* Build docs now live at ``docs/build/html``

0.1.0 (2014-05-12)
++++++++++++++++++

* Initial version. Supports very basic validation of incoming requests.
