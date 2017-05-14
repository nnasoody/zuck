# Zuck

:warning: **WIP** :warning:

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed
by adding `zuck` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [{:zuck, "~> 0.1.0"}]
end
```

## Configuration

```elixir
config :zuck, 
  app_id: "",
  app_secret: "",
  log: true,
  debug: true,
  version: "v2.9",
  endpoint: "https://graph.facebook.com/",
  http: [] # these will be passed to hackney
```

## Usage


### Basic example

```elixir
{:ok, user} = Zuck.get("/me", %{
  access_token: "TOKEN",
  fields: "name,email"
})
```

### Pagination trough streams

You can use the stream helpers to handle multipage data, very useful when getting ad insights or large lists of data:

```elixir
Zuck.get_stream("/act_ACCOUNT_ID/insights", %{
  access_token: "TOKEN",
  level: "ad",
  date_preset: "yesterday",
  fields: "ad_name"
})
|> Enum.map(fn ad -> ad.ad_name end)
```

Documentation can be generated with [ExDoc](https://github.com/elixir-lang/ex_doc)
and published on [HexDocs](https://hexdocs.pm). Once published, the docs can
be found at [https://hexdocs.pm/zuck](https://hexdocs.pm/zuck).

