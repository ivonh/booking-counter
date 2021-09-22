# booking-counter
This is a booking counter if else with try blocks.
    //first remove all existing rows
            if(bookingTableModel.getRowCount()>0)
            {
                for (int i = bookingTableModel.getRowCount() - 1; i > -1; i--)
                {
                    bookingTableModel.removeRow(i);
                }
            }
            //New row data
            if (bb_Read.getObjectDataSet() !=null)
            {
                //add data
                for (int row = 0; row < bb_Read.getObjectDataSet().length; row++)
                {
                    bookingTableModel.addRow(bb_Read.getObjectDataSet()[row]);
                }
                //update
                bookingTableModel.fireTableDataChanged();
            }
        }
        else
        {
            //no records found
        }
        availableLabel.setText("Availability for this Charter is: " + totalCapacity);
        String bookCounterSql = "Select MAX(Counter) as bookID from bookings;";   
        getCountData(bookCounterSql);
        
        //check for errors
        if(bb_Read.getErrorMessage().length() > 0)
        {
            System.out.println(bb_Read.getErrorMessage());
        }
