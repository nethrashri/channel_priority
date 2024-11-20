
Core Features
Date Range:

Generates timestamps from January 1, 2023, to November 30, 2024.
Uses 15-minute intervals (freq='15T').
Service Groups and Device Types:

Defines service groups (Gaming, Streaming, Social Media, Shopping, Software) with their corresponding service names (e.g., Netflix, Fortnite).
Assigns a device_type dynamically based on the service group (e.g., TV for Streaming).
User and MAC Address:

Simulates one user (user1) with five MAC addresses, which are assigned randomly for each session.
Usage Patterns
1. Weekday Rules (Monday to Friday):
7:00 AM - 7:30 AM: Uses either Social Media or Streaming.
9:00 AM - 7:00 PM: Exclusively uses Software.
7:00 PM - 10:00 PM: Alternates between:
Gaming on even weekdays (Monday, Wednesday, Friday).
Streaming on odd weekdays (Tuesday, Thursday).
8:00 PM - 9:30 PM: Uses additional Streaming.
11:00 PM - 11:30 PM on Fridays: Falls back to Shopping.
2. Weekend Rules (Saturday and Sunday):
7:00 AM - 7:30 AM: Uses either Social Media or Streaming.
9:00 AM - 7:00 PM: Uses Software.
7:00 PM - 11:00 PM: Exclusively uses Netflix.
Other times: Falls back to either Social Media or Streaming.
Generated Features
Usage Metrics:

usage_minutes: Randomly generated between 1 and 60.
usage_percentage: Computed as: \text{usage_percentage} = \min\left(\frac{\text{usage_minutes}}{60} \times 100, 100\right)
Network Features:

signal_strength: Random value between -60 and -40 dBm.
packet_loss_rate: Random value between 0 and 1.
latency: Random value between 10 and 50 milliseconds.
jitter_ms: Random value between 0 and 10 milliseconds.
traffic_spike: Boolean (0 or 1).
bandwidth_speed_per_sec_mbps: Random value between 5 and 15.
buffer_occupancy: Random value between 0 and 1.
Output Dataset
Filename:

The dataset is saved as netflix_user1_friday_shopping.csv.
Columns:

Column Name	Description
user	Username (user1).
timestamp	Timestamp of the session.
mac_address	Randomly assigned MAC address.
service_group	The service group (e.g., Streaming, Gaming).
service_name	The specific service name (e.g., Netflix, Amazon).
device_type	The type of device used (e.g., TV, Mobile).
usage_minutes	Number of minutes the service was used.
usage_percentage	Percentage of an hour used (0-100).
signal_strength	Signal strength in dBm.
packet_loss_rate	Packet loss rate (fraction).
latency	Network latency in milliseconds.
jitter_ms	Network jitter in milliseconds.
traffic_spike	Indicates traffic spike (0 or 1).
bandwidth_speed_per_sec_mbps	Bandwidth in Mbps.
buffer_occupancy	Buffer occupancy (fraction).


Key Highlights
Dynamic Assignment:

service_group and service_name are dynamically assigned based on time-based rules.
device_type is chosen logically based on service_group.
Friday Special:

Adds a unique fallback for Shopping between 11:00 PM and 11:30 PM.
Network Simulations:

Simulates realistic network conditions and service usage.