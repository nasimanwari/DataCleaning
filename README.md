# Nashville Housing Data Cleaning Script

This script cleans the Nashville Housing data set by performing the following tasks:

1. Standardizes the date format of the `SaleDate` column.
2. Populates the `PropertyAddress` column with data from the `OwnerAddress` column where `PropertyAddress` is null.
3. Breaks out the `PropertyAddress` column into three separate columns: `PropertySplitAddress`, `PropertySplitCity`, and `PropertySplitState`.
4. Breaks out the `OwnerAddress` column into three separate columns: `OwnerSplitAddress`, `OwnerSplitCity`, and `OwnerSplitState`.
5. Changes the values in the `SoldAsVacant` column from `Y` and `N` to `Yes` and `No`.
6. Removes duplicate rows from the data set.
7. Deletes the `OwnerAddress`, `TaxDistrict`, and `PropertyAddress` columns.

The script is written in T-SQL and can be run in SQL Server Management Studio.

## To Run the Script

1. Open SQL Server Management Studio.
2. Connect to the database that contains the `NashvilleHousing` table.
3. Right-click on the `NashvilleHousing` table and select "Open Table".
4. Copy and paste the script into the query window.
5. Click the "Execute" button.

The script will run and the data set will be cleaned.

## Data Cleaning Notes

* The `SaleDate` column was originally in a variety of formats. The script standardizes the format to `YYYY-MM-DD`.
* The `PropertyAddress` column was missing data for some rows. The script populates the missing data by joining the `NashvilleHousing` table to itself on the `ParcelID` column.
* The `PropertyAddress` and `OwnerAddress` columns were both in the format `Address, City, State`. The script breaks these columns out into three separate columns for each address.
* The `SoldAsVacant` column originally contained the values `Y` and `N`. The script changes these values to `Yes` and `No` for consistency.
* The script removes duplicate rows from the data set based on the `ParcelID`, `PropertyAddress`, `SalePrice`, `SaleDate`, and `LegalReference` columns.
* The script deletes the `OwnerAddress`, `TaxDistrict`, and `PropertyAddress` columns because they are no longer needed.
