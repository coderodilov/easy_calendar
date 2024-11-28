# Easy Tech Calendar

A highly customizable and user-friendly calendar widget for Flutter. The `easy_tech_calendar` widget allows users to select dates in multiple modes (range selection or multi-selection) and offers a variety of customization options like colors, borders, and locale support.

## Features

- **Range Selection**: Allows users to select a date range.
- **Multi-Selection**: Users can select multiple individual dates.
- **Customization**: Customize the appearance of selected and unselected days, borders, and text colors.
- **Localization**: Supports localization for week days and month names.
- **Year Selector**: Allows users to select a year and navigate through the months of that year.
- **Built-in Controller**: Manage selected days with the `EasyCalendarController`.

## Installation

To add the `easy_tech_calendar` package to your Flutter project, add the following line to your `pubspec.yaml` file:

```yaml
dependencies:
  flutter:
    sdk: flutter
  easy_tech_calendar: ^1.0.0 # Check for the latest version
  intl: ^0.18.0 # Required for date formatting
```

## Usage
Step 1: Import the package

import 'package:easy_tech_calendar/easy_tech_calendar.dart';
import 'package:flutter/material.dart';

Step 2: Create an EasyCalendarController
The EasyCalendarController is used to manage selected dates. It can be used to handle multi-selection or range selection mode.

```dart
class EasyCalendarController {
     List<DateTime> selectedDays = []; // Multi-selection mode
     DateTime? selectedMinDate; // Range selection (min date)
     DateTime? selectedMaxDate; // Range selection (max date)
}
```

Step 3: Use the EasyCalendar widget
The EasyCalendar widget can be placed inside your widget tree. 
You can toggle between range mode and multi-selection mode, and customize the calendar's appearance with various properties.


```dart
import 'package:easy_tech_calendar/easy_tech_calendar.dart';
import 'package:flutter/material.dart';

class CalendarPage extends StatefulWidget {
  @override
  _CalendarPageState createState() => _CalendarPageState();
}

class _CalendarPageState extends State<CalendarPage> {
  final EasyCalendarController _controller = EasyCalendarController();
  bool _rangeMode = false;
  String _locale = 'en'; // Set locale for the calendar (e.g., 'en', 'ru', 'uz')

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Easy Calendar'),
        actions: [
          IconButton(
            icon: Icon(Icons.calendar_today),
            onPressed: () {
              setState(() {
                _rangeMode = !_rangeMode;
              });
            },
          ),
        ],
      ),
      body: Padding(
        padding: const EdgeInsets.all(8.0),
        child: EasyCalendar(
          rangeMode: _rangeMode, // Toggle range mode
          locale: _locale, // Set locale (e.g., 'en', 'ru', 'uz')
          controller: _controller,
          selectedDayColor: Colors.blue, // Customize selected day color
          selectedDayBorderColor: Colors.blue.shade700, // Customize selected day border
          selectedDayTextColor: Colors.white, // Customize selected day text color
          unSelectedDayColor: Colors.white, // Customize unselected day color
          unSelectedDayBorderColor: Colors.grey.shade300, // Customize unselected day border
          unSelectedDayTextColor: Colors.black, // Customize unselected day text color
          disabledDaysColor: Colors.grey.shade200, // Customize disabled day color
          disabledDaysTextColor: Colors.grey, // Customize disabled day text color
          yearTitleColor: Colors.black87, // Customize year title color
          monthTitleColor: Colors.black87, // Customize month title color
          weakDaysColor: Colors.grey.shade500, // Customize weak day text color
        ),
      ),
    );
  }
}

```


Step 4: Use the EasyCalendar widget
For using Localization u should init localization to your app first.

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return  const MaterialApp(
      debugShowCheckedModeBanner: false,
      supportedLocales: [
        Locale('en'),
        Locale('uz'),
      ],
      localizationsDelegates: [
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
        GlobalCupertinoLocalizations.delegate,
      ],
      home: HomePage()
    );
  }
}
```

![Screenshot_20241128_104335](https://github.com/user-attachments/assets/f5b27f52-8a5e-4497-beba-a3215201a428)







