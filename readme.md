data engineer project lấy dataset từ những vụ tai nạn để analyze accident data và nguyên nhân gây ra tai nạn

Ý tưởng là tạo ra một hồ dữ liệu tối ưu giúp người dùng phân tích dữ liệu về tai nạn và xác định nguyên nhân gốc rễ của các tai nạn. Mục tiêu chính của dự án này là xây dựng một pipeline dữ liệu từ đầu đến cuối có khả năng làm việc với khối lượng dữ liệu lớn. làm sạch, biến đổi và tải dữ liệu vào datalake  trên S3. datalake sẽ bao gồm các bảng logic được phân vùng theo các cột cụ thể để tối ưu hóa thời gian truy vấn.



data model :

Fact table

1.accidents
accident_id; string; unique identifier of the accident record; Primary Key
datetime; datetime; shows start time of the accident in local time zone
severity; int; shows the severity of the accident, a number between 1 and 4
distance; int; the length of the road extent affected by the accident
description; string; shows natural language description of the accident
temperature: Shows the temperature (in Fahrenheit)
wind_speed; int; shows wind speed (in miles per hour)
precipitation; int; shows precipitation amount in inches, if there is any.
airport_code; string; 4-character airport code; Foreign Key
city_id; int; city identifier; Foreign Key
weather_condition_id; int; identifier; Foreign Key

Dimension tables
1.cities
city_id; int; unique id of city; Primary Key, auto-incremented
city_name; string; name of the city
state_code; string; 2-letter code of the state
total_population; int: total population of the city
2.airports
airport_code; string; 4-character unique airport code; Primary Key
type; string; type of airport (small, medium, large)
name; string; name of the airport
state_code; string; the state airport belongs to, 2-letter code
municipality; string; municipality the airport belongs to
3.weather_conditions
weather_condition_id; int; identifier; Primary Key
condition; string; shows the weather condition (rain, snow, thunderstorm, fog, etc.)
