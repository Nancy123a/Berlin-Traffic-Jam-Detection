This project focuses on detecting traffic jams in Berlin using real-time sensor data from the [Telraam API](https://documenter.getpostman.com/view/8210376/TWDRqyaV). The main goal is to identify traffic anomalies across different road segments and time intervals to improve traffic management, public safety, and urban planning.

The methodology involves collecting and processing hourly and quarterly aggregated traffic data, including vehicle counts and speed information. Key limitations include the absence of raw image or video data and variable sensor uptime, which can lead to missed data. Data enrichment with TomTom Georeverse API was used to add street names to segment coordinates. Preprocessing steps included excluding data with zero uptime, creating time intervals (Night, Morning, Midday, Afternoon, Evening), and normalizing car counts by uptime.

Traffic anomalies were initially identified using the Interquartile Range (IQR) method on normalized and standardized car traffic data. An autoencoder was then employed for more sophisticated anomaly detection, trained on normal traffic data to identify anomalies based on higher reconstruction errors. Recall was prioritized during threshold tuning to minimize false negatives, as missing true anomalies poses greater risks. The optimal threshold of 0.0079 resulted in a recall of 0.975.

Analysis of results revealed:
* 🚗 **Traffic Variations:** High coefficient of variation (CV) indicated volatile traffic, especially during night, morning, and evening, while midday traffic was more consistent.
* 🚨 **Anomaly Hotspots:** 'Simplon', 'Handjery', and 'Galenus' segments showed the highest anomaly counts, indicating unstable traffic patterns.
* 📈 **Temporal Distribution:** Midday (13:00–14:00) and rush hours (5–9 AM, 4–6 PM) experienced the most anomalies. Weekdays, particularly Fridays, had more anomalies than weekends. September and winter months like January also showed increased anomalies.
* 📊 **Model Performance:** The autoencoder achieved 99% overall accuracy, with a high recall of 0.96 for traffic jams, demonstrating effective detection with minimal false negatives.

The project suggests prioritizing high-anomaly segments for traffic management, increasing sensor uptime (V2), optimizing threshold settings, and focusing on peak hours for disruption monitoring. These findings can inform urban planning and infrastructure improvements to enhance traffic flow in Berlin.
