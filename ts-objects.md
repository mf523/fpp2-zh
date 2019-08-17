# 2.1 ts objects
A time series can be thought of as a list of numbers, along with some information about what times those numbers were recorded. This information can be stored as a `ts` object in R.

Suppose you have annual observations for the last few years:

**Year** | **Observation**
-----|-----------
2012 | 123
2013 | 39
2014 | 78
2015 | 52
2016 | 110

We turn this into a `ts` object using the `ts()` function:

```R
y <- ts(c(123,39,78,52,110), start=2012)
```

If you have annual data, with one observation per year, you only need to provide the starting year (or the ending year).

For observations that are more frequent than once per year, you simply add a `frequency` argument. For example, if your monthly data is already stored as a numerical vector `z`, then it can be converted to a `ts` object like this:

```R
y <- ts(z, start=2003, frequency=12)
```

Almost all of the data used in this book is already stored as `ts` objects. But if you want to work with your own data, you will need to use the `ts()` function before proceeding with the analysis.

# Frequency of a time series
The “frequency” is the number of observations before the seasonal pattern repeats. <sup><a name="fnref1">1</a></sup> When using the `ts()` function in R, the following choices should be used.

**Data** | **frequency**
---------|--------------
Annual | 1
Quarterly | 4
Monthly	| 12
Weekly | 52


Actually, there are not 52 weeks in a year, but 365.25/7 = 52.18 on average, allowing for a leap year every fourth year. But most functions which use ts objects require integer frequency.

If the frequency of observations is greater than once per week, then there is usually more than one way of handling the frequency. For example, data with daily observations might have a weekly seasonality (frequency = 7) or an annual seasonality (frequency = 365.25). Similarly, data that are observed every minute might have an hourly seasonality (frequency = 60), a daily seasonality (frequency = 24 × 60 = 1440), a weekly seasonality (frequency = 24 × 60 × 7 = 10080) and an annual seasonality (frequency = 24 × 60 × 365.25 = 525960). If you want to use a ts object, then you need to decide which of these is the most important.

In [chapter 11](advanced.md) we will look at handling these types of multiple seasonality, without having to choose just one of the frequencies.

------------------------
<a name="fn1"></a>
1. This is the opposite of the definition of frequency in physics, or in Fourier analysis, where this would be called the “period”.<a name="fnref1">↩</a>
