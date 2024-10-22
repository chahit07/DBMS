import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import org.apache.poi.ss.usermodel.*;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;

public class ExcelFileReader {

    private String filePath;

    // Constructor to set the file path
    public ExcelFileReader(String filePath) {
        this.filePath = filePath;
    }

    // Method to read the Excel file and display its content
    public void readExcelFile() {
        try (FileInputStream fileInputStream = new FileInputStream(new File(filePath))) {

            // Create a Workbook instance for the Excel file
            Workbook workbook = new XSSFWorkbook(fileInputStream);

            // Get the number of sheets in the workbook
            int numberOfSheets = workbook.getNumberOfSheets();

            // Iterate through all sheets
            for (int i = 0; i < numberOfSheets; i++) {
                Sheet sheet = workbook.getSheetAt(i);
                String sheetName = sheet.getSheetName();
                System.out.println("Sheet: " + sheetName);

                // Iterate through rows and cells of the current sheet
                for (Row row : sheet) {
                    for (Cell cell : row) {
                        // Handle cell types and print the value accordingly
                        printCellValue(workbook, cell);
                    }
                    System.out.println();
                }
                System.out.println("End of Sheet: " + sheetName + "\n");
            }

            // Close the workbook
            workbook.close();

        } catch (IOException e) {
            System.err.println("Error reading the Excel file: " + e.getMessage());
            e.printStackTrace();
        }
    }

    // Method to print the value of a cell based on its type
    private void printCellValue(Workbook workbook, Cell cell) {
        switch (cell.getCellType()) {
            case STRING:
                System.out.print(cell.getStringCellValue() + "\t");
                break;
            case NUMERIC:
                if (DateUtil.isCellDateFormatted(cell)) {
                    System.out.print(cell.getDateCellValue() + "\t");
                } else {
                    System.out.print(cell.getNumericCellValue() + "\t");
                }
                break;
            case BOOLEAN:
                System.out.print(cell.getBooleanCellValue() + "\t");
                break;
            case FORMULA:
                // Evaluate the formula and print its result
                FormulaEvaluator evaluator = workbook.getCreationHelper().createFormulaEvaluator();
                CellValue cellValue = evaluator.evaluate(cell);
                printFormulaResult(cellValue);
                break;
            case BLANK:
                System.out.print("BLANK\t");
                break;
            default:
                System.out.print("Unknown Cell Type\t");
                break;
        }
    }

    // Method to print the result of a formula
    private void printFormulaResult(CellValue cellValue) {
        switch (cellValue.getCellType()) {
            case NUMERIC:
                System.out.print(cellValue.getNumberValue() + "\t");
                break;
            case STRING:
                System.out.print(cellValue.getStringValue() + "\t");
                break;
            case BOOLEAN:
                System.out.print(cellValue.getBooleanValue() + "\t");
                break;
            default:
                System.out.print("Unknown Formula Result\t");
                break;
        }
    }
}
