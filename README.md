# strongDM SDK for Java

This is the official [strongDM](https://www.strongdm.com/) SDK for the Java
programming language.

Learn more with our [📚strongDM API docs](https://www.strongdm.com/docs/api/) or
[📓browse the SDK
reference](https://strongdm.github.io/strongdm-sdk-java-docs/).

## Installation

Gradle:

```gradle
repositories {
    mavenCentral()
}

dependencies {
    compile "io.github.strongdm:strongdm-sdk-java:${strongdm.version}"
	...
```

strongDM uses [semantic versioning](https://semver.org/). We do not guarantee
compatibility between major versions. Be sure to use version constraints to pin
your dependency to the desired major version of the strongDM SDK.

## Authentication

If you don't already have them you will need to generate a set of API keys,
instructions are here: [API
Credentials](https://www.strongdm.com/docs/admin-guide/api-credentials/)

Add the keys as environment variables; the SDK will need to access these keys
for every request.

```bash
$ export SDM_API_ACCESS_KEY=<YOUR ACCESS KEY>
$ export SDM_API_SECRET_KEY=<YOUR SECRET KEY>
```

## List Users

The following code lists all registered users:

```java
try {
	client = new Client(System.getenv("SDM_API_ACCESS_KEY"),System.getenv("SDM_API_SECRET_KEY"));
	Iterable<Account> resp = client.accounts().list("");
	for (Account n : resp) {
		if (n instanceof User) {
			User u = (User)n;
			System.out.println(u.getEmail());
		}
	}
} catch (Exception e) {
	e.printStackTrace();
}
```

## Useful Links

- Documentation: [javadoc](https://strongdm.github.io/strongdm-sdk-java-docs/)
- [Migrating from v2 to v3](https://github.com/strongdm/strongdm-sdk-java/releases/tag/v3.0.0)
- [Migrating from Role Grants to Access Rules](https://github.com/strongdm/strongdm-sdk-java/wiki/Migrating-from-Role-Grants-to-Access-Rules)
- Examples: [GitHub - strongdm/strongdm-sdk-java-examples](https://github.com/strongdm/strongdm-sdk-java-examples)
  1.  [Managing Resources](https://github.com/strongdm/strongdm-sdk-java-examples/tree/master/1_managing_resources)
  2.  [Managing Accounts](https://github.com/strongdm/strongdm-sdk-java-examples/tree/master/2_managing_accounts)
  3.  [Managing Roles](https://github.com/strongdm/strongdm-sdk-java-examples/tree/master/3_managing_roles)
  4.  [Managing Gateways](https://github.com/strongdm/strongdm-sdk-java-examples/tree/master/4_managing_gateways)

## License

[Apache 2](https://github.com/strongdm/strongdm-sdk-java/blob/master/LICENSE)

## Contributing

Currently, we are not accepting pull requests directly to this repository, but
our users are some of the most resourceful and ambitious folks out there. So, if
you have something to contribute, find a bug, or just want to give us some
feedback, please email <support@strongdm.com>.
