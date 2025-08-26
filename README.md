# How-to-apply-initial-multi-column-sorting-in-Flutter-DataTable-SfDataGrid

In this article, we will show how to apply initial multi-column sorting in [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) with the necessary properties. The DataGrid supports programmatic column sorting. You can manually define [SortColumnDetails](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SortColumnDetails-class.html) objects and add them to the [SfDataGrid.source.sortedColumns](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/sortedColumns.html) collection. The DataGrid then sorts the data based on the SortColumnDetails objects in this collection. By handling this in the [initState](https://api.flutter.dev/flutter/widgets/State/initState.html) method, you can define a multi-column sort order that is automatically applied when the DataGrid is first rendered.

```dart
  @override
  void initState() {
    super.initState();
    employees = getEmployeeData();
    employeeDataSource = EmployeeDataSource(employeeData: employees);
    //Initial-multi-column-sorting
    employeeDataSource.sortedColumns.addAll([
      SortColumnDetails(
        name: 'id',
        sortDirection: DataGridSortDirection.ascending,
      ),
      SortColumnDetails(
        name: 'name',
        sortDirection: DataGridSortDirection.ascending,
      ),
    ]);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
        source: employeeDataSource,
        columnWidthMode: ColumnWidthMode.fill,
        columns: <GridColumn>[
          GridColumn(
            columnName: 'id',
            label: Container(
              padding: EdgeInsets.all(16.0),
              alignment: Alignment.center,
              child: Text('ID'),
            ),
          ),
          GridColumn(
            columnName: 'name',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Name'),
            ),
          ),
          GridColumn(
            columnName: 'designation',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Designation', overflow: TextOverflow.ellipsis),
            ),
          ),
          GridColumn(
            columnName: 'salary',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Salary'),
            ),
          ),
        ],
      ),
    );
  }
```
You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-apply-initial-multi-column-sorting-in-Flutter-DataTable-SfDataGrid.git).