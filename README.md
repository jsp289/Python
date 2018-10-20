# Read a file and determine the average response time per ticket for each hour of the day
# 1) Nested function get_data opens & reads file, converts and returns datetime tuples.
# 2) Create an empty list data_tuples and populate it with two columns getting rid of the comma delimiter.
# 3) Convert the string into a datetime object. Only keep the hour as the first element, and convert second into a float.
# 4) Create a dictionary hour has hours of the day as keys, and number of tickets for that hour and sum of response times for each ticket.
# 5) Return average response time for each hour of the days.

def get_ticket_avg(filename):
    def get_data(filename):
        data_tuples = list()
        with open (filename, 'r') as f:
            for line in f:
                 data_tuples.append(line.strip().split(','))
        import datetime
        format_str = "%H-%M-%D %H:%M:%S"
        data_tuples = [(datetime.datetime.stptime(x[0],str_format).hour, float(x[1])) for x in data_tuples]
        return data_tuples
    hours = dict()
    if item in get_data(filename): 
        hours [item[0]][0] +=1
        hours[item[0]][1] +=item[1]
        else hours[item[0]] = [1,item[1]]
    return [(key,value[1]/value[0] for key,value in hours.items())]
