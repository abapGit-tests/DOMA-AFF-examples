# abapGit DOMA Test Repository

This repository contains example DOMA (Domain) objects in AFF JSON format for testing the DOMA AFF serializer implementation.

## Test Files

### Simple Examples
- **zdoma_example_simple.doma.json** - Basic character domain (CHAR, length 10)
- **zdoma_example_date.doma.json** - Date domain (DATS, length 8)

### Examples with Fixed Values
- **zdoma_example_with_values.doma.json** - Character domain with 3 fixed values (RED, GRN, BLU)
- **zdoma_example_numeric.doma.json** - Numeric domain with value intervals (1000-1999, 2000-2999)

### Examples with Special Features
- **zdoma_example_conversion.doma.json** - Domain with ALPHA conversion exit routine
- **zdoma_example_currency.doma.json** - Currency domain (CURR) with decimals and negative values

## Testing

To test the DOMA AFF serializer:

1. Enable the AFF feature flag in abapGit settings
2. Clone this repository into your SAP system using abapGit
3. Verify that domains are created correctly with all attributes
4. Export the domains and verify JSON format matches expected structure

## AFF Format Structure

All DOMA files follow the SAP ABAP File Format v1 specification:

```json
{
  "formatVersion": "1",
  "header": {
    "description": "Domain description (max 60 chars)",
    "originalLanguage": "E"
  },
  "format": {
    "dataType": "CHAR|NUMC|DATS|CURR|...",
    "length": 10,
    "decimals": 0  // optional
  },
  "outputCharacteristics": {  // optional
    "length": 10,
    "conversionRoutine": "ALPHA",
    "caseSensitive": false,
    "negativeValues": false
  },
  "fixedValues": [  // optional
    {
      "fixedValue": "VALUE",
      "description": "Description"
    }
  ],
  "fixedValueIntervals": [  // optional
    {
      "lowLimit": "0000",
      "highLimit": "9999",
      "description": "Range description"
    }
  ],
  "valueTable": {  // optional
    "name": "TABLE_NAME"
  }
}
```

## Data Types Supported

The DOMA AFF serializer supports all 37 ABAP data types including:
- Character types: CHAR, NUMC, LANG
- Date/Time types: DATS, TIMS, DATN, TIMN, UTCLONG
- Numeric types: INT1, INT2, INT4, INT8, DEC, FLTP
- Currency/Quantity: CURR, QUAN, CUKY, UNIT
- String types: STRING, RAWSTRING
- Decimal float: DECFLOAT16, DECFLOAT34
- And many more...

## Related Implementation

- Implementation PR: [Link to be added]
- AFF Specification: https://github.com/SAP/abap-file-formats/tree/main/file-formats/doma
