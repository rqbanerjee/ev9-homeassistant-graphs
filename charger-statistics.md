# Charger Statistics
I use an [Emporia](https://www.amazon.com/dp/B0CKKPTDPK/ref=dp_iou_view_item?ie=UTF8&th=1}) charger that provides a sensor "sensor.evcharger_energy_this_month" that can be used to calculate how much money you have spent on electricity.

To get an accurate price / per kilowatt hour, instead of using the utility company's stated price per kWh, I prefer to include all the taxes, riders, and fees they lump into your bill. To do that, divide (total_bill_amount) / (net_supplied_energy - net_supplied_customer_to_grid) since I have solar panels as well. Our utility quotes $0.13/kWh on the rate schedule, but actual price is $0.159/kWh with fees and riders included. 

![Charger Statistics](static/charger_stats.png)
