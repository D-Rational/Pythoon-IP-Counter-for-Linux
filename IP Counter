#!/usr/bin/env python3

import sys
import re
from prettytable import PrettyTable


x=PrettyTable()
f= sys.argv[1]

fopen= open(f, 'r')

def parser(fopen):
    #ipcount= ipcount + 1
    iptotal = 0
    #declaring the regex patten for IP addresses
    ips= re.compile("\\d{1,3}\\.\\d{1,3}\\.\\d{1,3}\\.\\d{1,3}")
    ip_rec={}

    #extracting ips from each line of the file
    for line in fopen:
        line = line.strip()
        ip_found = ips.search(line)
        if ip_found:
            iptotal = iptotal + 1
            ip = ip_found.group(0)
            ip_rec[ip] = ip_rec.get(ip,0)+1
        sorted_ip_rec = sorted(ip_rec.items(), key = lambda kv:(kv[1], kv[0]))
#pretty tables
    x=PrettyTable()
    x.field_names = ["percentage", "count", "ipp"]
    
    for i in sorted_ip_rec:
        percentage = (float(i[1]/iptotal) * 100)
        index = str(percentage).index(".")
        #rounds the percentage off to the nearest 1000th place
        percentage = str(percentage)[0:index] + str(percentage)[index:index +4] +'%'
        i = (i, percentage)
        ipp=i[0][0]
        count = str(i[0][1])
        percentage = str(percentage)
        #print (ipp)
        #print(count)
        x.add_row([percentage, count, ipp])
    print(x)

parser(fopen)
