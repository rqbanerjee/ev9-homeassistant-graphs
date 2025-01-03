# Charger Statistics
I use an [Emporia](https://www.amazon.com/dp/B0CKKPTDPK/ref=dp_iou_view_item?ie=UTF8&th=1}) charger that provides a sensor "sensor.evcharger_energy_this_month" that can be used to calculate how much money you have spent on electricity in the calendar month.

## Other Chargers
If you have a different charger, like a Chargepoint for example, the metrics they provide will be different.

Please send a pull request to this repo if you have suggestions on how to incorporate data from other chargers.

## Accurate utility pricing
To get an accurate price / per kilowatt hour, instead of using the utility company's stated price per kWh, I prefer to include all the taxes, riders, and fees they lump into your bill. To do that, divide (total_bill_amount) / (net_supplied_energy - net_supplied_customer_to_grid) since I have solar panels as well. Our utility quotes $0.13/kWh on the rate schedule, but actual price is $0.159/kWh with fees and riders included. 

![Charger Statistics](static/charger_stats.png)

## Helper Setup
1. Log into your Home Assistant dashboard
1. Click *Settings* -> *Devices & services*
1. On the top navigation bar, click *Helpers*
1. Click *Create Helper*
1. Click *Template* -> *Template sensor*
1. Name it something like "evcharger_cost_this_month" or similar
1. Paste and *customize* these values:
```
        {% set energy_this_month = states('sensor.evcharger_energy_this_month') | float %}

        {{ ((energy_this_month) * 0.1544904) | round(2, default=2) }}
```
