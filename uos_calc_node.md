**Starting a Calculator Node**

1. Build the node according to instructions in https://github.com/UOSnetwork/uos.docs/blob/master/uosBPubuntu.md

2. Register your account as the calculator

```cleos push action eosio regcalc '["myaccname111", "https://myaccname111.com",40]' -p myaccname111```

3. Add the plugins to the config.ini

```
plugin = eosio::chain_api_plugin
plugin = eosio::history_api_plugin
plugin = eosio::uos_rates
```

4. Add your name and keys to the config.ini

```
calculator-name = myaccname111
calculator-public-key = EOS....
calculator-private-key = 5....
```

5. Run the node and wait for the synchronization

6. Contact the UOS developers to get voted in
