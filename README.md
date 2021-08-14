<h1 align="center"> Age in Minutes App </h1>
<p align="center"> Calculate your age in minutes by selecting your date of birth </p>

## Click Date Picker Function
```kotlin
fun clickDatePicker(view: View){
    val myCalendar = Calendar.getInstance()
    val year = myCalendar.get(Calendar.YEAR)
    val month = myCalendar.get(Calendar.MONTH)
    val day = myCalendar.get(Calendar.DAY_OF_MONTH)

    val dpd = DatePickerDialog(this,
        DatePickerDialog.OnDateSetListener {
                view, selectedYear, selectedMonth, selectedDayOfMonth ->

            val selectedDate = "$selectedDayOfMonth/${selectedMonth+1}/$selectedYear"
            tvSelectedDate.text = selectedDate

            val sdf = SimpleDateFormat("dd/MM/yyyy", Locale.ENGLISH)
            val theDate = sdf.parse(selectedDate)

            val selectedDateInMinutes = theDate!!.time / 60000
            val currentDate = sdf.parse(sdf.format(System.currentTimeMillis()))
            val currentDateToMinutes = currentDate!!.time / 60000
            val differenceInMinutes = currentDateToMinutes - selectedDateInMinutes

            tvSelectedDateInMinutes.text = "$differenceInMinutes"

        }
        ,year
        ,month
        ,day)

    dpd.datePicker.maxDate = Date().time - 86400000
    dpd.show()
}
```
<p align="center"> Call function on button click event. </p>

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)

    btnDatePicker.setOnClickListener {
        clickDatePicker(it)
    }
}
```

<p align="center">
  <img src='https://github.com/ayhanunal/AgeInMinutes-App/blob/main/ss/screen_record.gif' width=400 heihgt=500> 
</p>
