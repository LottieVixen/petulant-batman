### NOT COMPETE
# By Websten from forums
#
# Given your birthday and the current date, calculate your age in days. 
# Account for leap days. 
#
# Assume that the birthday and current date are correct dates (and no 
# time travel). 
#

def leapyear(year):
    #if (year is not divisible by 4) then (it is a common year)
    if str(year/4.0)[str(year/4.0).find('.')+1:] != '0':
        return False
    if str(year/100.0)[str(year/100.0).find('.')+1:] != '0':
        return True
    if str(year/400.0)[str(year/400.0).find('.')+1:] != '0':
        return False
    return True

def leapyearsBetween(a,b):
    leaps = 0
    while a <= b:
        if leapyear(a):
            leaps = leaps + 1
        a = a + 1
    return leaps

def daysBetweenDates(year1, month1, day1, year2, month2, day2):
    years = year2 - year1
    months = month2 - month1
    days = day2 - day1
    leapyears = leapyearsBetween(year1,year2)
    days = days + leapyears
    days = days + years*365
    days = days + months
    #print 'y'+str(years)+',m'+str(months)+',d'+str(days)+',leaps'+str(leapyears)
    return days


# Test routine

def test():
    test_cases = [((2012,1,1,2012,2,28), 58), 
                  ((2012,1,1,2012,3,1), 60),
                  ((2011,6,30,2012,6,30), 366),
                  ((2011,1,1,2012,8,8), 585 ),
                  ((1900,1,1,1999,12,31), 36523)]
    for (args, answer) in test_cases:
        result = daysBetweenDates(*args)
        if result != answer:
            print "Test with data:", args, "failed"
        else:
            print "Test case passed!"

test()