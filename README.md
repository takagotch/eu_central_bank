### eu_central_bank
---

https://github.com/RubyMoney/eu_central_bank

```
gem install eu_central_bank
gem 'nokogiri', '1.6.8'

```

```ruby
require ''
eu_bank = EuCentralBank.new
Money.default_bank = eu_bank
money1 = Money.new(10)
money1.bank #eu_bank

eu_bank.update_rates

eu_bank.exchange(100, "CAD", "USD")
Money.us_dollar(100).exchange_to("CAD")

eu_bank.exchange_with(Money.new(100, "CAD"), "USD")
```

```ruby
cache = "/some/file/location/exchange_rates.xml"

eu_bank.save_rates(cache)

eu_bank.update_rates(cache)

if !eu_bank.rates_updated_at || eu_bank.rates_updated_at < Time.now - 1.days
  eu_bank.save_rates(cache)
  eu_bank.update_rates(cache)
end

eu_bank.exchange_with(Money.new(100, "CAD"), "USD")
```
