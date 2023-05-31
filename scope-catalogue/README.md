The hierarchy in these YAMLs is provider-focused, with each provider offering a scope, and within that, the clients that have access to this scope are defined.

>examples

- pricing

```yaml
Pricing.cost:
  - mobile.org
  - inventory.management
Pricing.cost.read:
  - webspa.digital
  - sales.dashboard
Pricing.cost.write:
  - admin.backend
Pricing.sell:
  - mobile.org
  - webspa.digital
Pricing.sell.read:
  - sales.dashboard
Pricing.sell.write:
  - admin.backend

```

- inventory

```yaml
Inventory.all:
  - mobile.org
  - webspa.digital
Inventory.read:
  - sales.dashboard
  - inventory.management
Inventory.write:
  - admin.backend
Inventory.stocklevel:
  - mobile.org
  - sales.dashboard
Inventory.stocklevel.read:
  - inventory.management
Inventory.stocklevel.write:
  - admin.backend

```

- order managmenet
  
```yaml
Order.all:
  - admin.backend
Order.read:
  - webspa.digital
  - sales.dashboard
Order.write:
  - mobile.org
Order.status:
  - mobile.org
  - webspa.digital
Order.status.read:
  - sales.dashboard
Order.status.write:
  - admin.backend

```


The design of managing scopes as provider-focused is premised on the intention to vest the full control of API accessibility in the hands of the API providers. Each YAML file, corresponding to a particular API provider, outlines the allocation of scopes to various clients.

This approach is significantly beneficial as it allows us to leverage a feature like CODEOWNERS. The CODEOWNERS file is a mechanism of GitLab that defines the individuals or teams responsible for the code in a project. By this means, each scope assignment YAML file can have its designated "owner," ensuring that the corresponding API provider retains authority over their API's access.

This setup not only ensures accountability but also streamlines the review and approval process for changes to scope assignments. Any alterations proposed, such as via a pull request, can be directly routed to the appropriate API provider for review, ensuring they have a say on who gets access to their API.