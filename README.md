# Samples for the PDF Services Node.js SDK

This sample project helps you get started with the  PDF Services Node.js SDK.

The sample JS scripts illustrate how to perform PDF-related actions (such as converting to and from the PDF format) using
the SDK. **Please note that the PDF Services Node.js SDK supports only server side use cases.**

## Prerequisites
The sample application has the following requirements:
* Node.js : Version 18.0 or above. Node installation instructions can be found
  [here](https://nodejs.org/en/download/).


## Authentication Setup

The credentials file for the samples is ```pdfservices-api-credentials.json```.
Before the samples can be run, set the environment variables `PDF_SERVICES_CLIENT_ID` and `PDF_SERVICES_CLIENT_SECRET`
from the `pdfservices-api-credentials.json` file downloaded at the end of creation of credentials via
[Get Started](https://www.adobe.io/apis/documentcloud/dcsdk/gettingstarted.html?ref=getStartedWithServicesSdk) workflow
by running the following commands :

1. For MacOS/Linux Users :
```$xlst
export PDF_SERVICES_CLIENT_ID=<YOUR CLIENT ID>
export PDF_SERVICES_CLIENT_SECRET=<YOUR CLIENT SECRET>
```

2. For Windows Users :
```$xlst
set PDF_SERVICES_CLIENT_ID=<YOUR CLIENT ID>
set PDF_SERVICES_CLIENT_SECRET=<YOUR CLIENT SECRET>
```

## Client Configurations

The SDK supports setting up custom request timeout for the API calls. Please refer this
[section](#create-a-pdf-file-from-a-docx-file-by-providing-custom-value-for-timeouts) to know more.

The SDK also supports setting up Proxy Server configurations which helps in successful API calls for network where all
outgoing calls have to go through a proxy else, they are blocked. Please
refer this [section](#create-a-pdf-file-from-a-docx-file-by-providing-proxy-server-settings) to
know more.

Additionally, SDK can be configured to process the documents in the specified region. Please refer this
[section](#export-a-pdf-file-to-a-docx-file-by-providing-the-region) section to know more.

## Quota Exhaustion

If you receive ServiceUsageError during the Samples run, it means that trial credentials have exhausted their usage quota.
Please [contact us](https://www.adobe.com/go/pdftoolsapi_requestform) to get paid credentials.

## Build with npm

Run the following command to build the project:
```$xslt
npm install
```

Note that the PDF Services SDK is listed as a dependency in the package.json and will be downloaded automatically.

## A Note on Logging
For logging, this SDK uses the [log4js API](https://www.npmjs.com/package/log4js) .
Upon running, the SDK searches for a file ```config/pdfservices-sdk-log4js-config.json``` in the working directory, and reads the
logging properties from there. If no configuration file is provided, default logging, i.e. logging INFO logs to the console is enabled. The clients can change the logging settings as per their needs.

## Running the samples

The following sub-sections describe how to run the samples. Prior to running the samples, check that the configuration
file is set up as described above and that the project has been built.

The samples code is available under the ```src``` folder. Test
files used by the samples can be found in the ```resources``` folder. When executed, all samples create an ```output```
child folder under the project root directory to store their results.

### Create a PDF File
These samples illustrate how to convert files of some formats to PDF. Refer the sdk documentation of create-pdf-operation.js
to see the list of all supported media types which can be converted to PDF.

#### Create a PDF File From a DOCX File

The sample script ```create-pdf-from-docx.js``` creates a PDF file from a DOCX file.

```$xslt
node src/createpdf/create-pdf-from-docx.js
```

#### Create a PDF File From a DOCX File with options

The sample script ```create-pdf-from-docx-with-options.js``` creates a PDF file from a DOCX file by setting documentLanguage as
the language of input file.

```$xslt
node src/createpdf/create-pdf-from-docx-with-options.js
```

####  Create a PDF File From a PPTX File

The sample script ```create-pdf-from-pptx.js``` creates a PDF file from a PPTX file.

```$xslt
node src/createpdf/create-pdf-from-pptx.js
```

### Create a PDF File From HTML
These samples illustrate how to convert HTML to PDF.
Refer the [HTML to PDF API documentation](https://developer.adobe.com/document-services/docs/apis/#tag/Html-to-PDF/operation/pdfoperations.htmltopdf)
to see instructions on the structure of the zip file.

#### Create a PDF File From Static HTML file with inline CSS

The sample script ```html-with-inline-css-to-pdf.js``` creates a PDF file from an input HTML file with inline CSS.

```$xslt
node src/htmltopdf/html-with-inline-css-to-pdf.js
```

#### Create a PDF File From HTML specified via URL

The sample script ```html-to-pdf-from-url.js``` creates a PDF file from an HTML specified via URL.

```$xslt
node src/htmltopdf/html-to-pdf-from-url.js
```

#### Create a PDF File From Static HTML (via Zip Archive)

The sample script ```static-html-to-pdf.js``` creates a PDF file from a zip file containing the input HTML file and its resources.
Please refer the sdk documentation of create-pdf-operation.js to see instructions on the structure of the zip file.

```$xslt
node src/htmltopdf/static-html-to-pdf.js
```

#### Create a PDF File From Dynamic HTML (via Zip Archive)

The sample script ```dynamic-html-to-pdf.js``` converts a zip file, containing the input HTML file and its
resources, along with the input data to a PDF file. The input data is used by the javascript in the HTML file to
manipulate the HTML DOM, thus effectively updating the source HTML file. This mechanism can be used to provide data to
the template HTML dynamically and then, convert it into a PDF file.

```$xslt
node src/htmltopdf/dynamic-html-to-pdf.js
```

### Export PDF To Other Formats
These samples illustrate how to export PDF files to other formats. Refer to the documentation of export-pdf-operation.js
and export-pdf-to-images-operation.js for supported export formats.

#### Export a PDF File To a DOCX File

The sample script ```export-pdf-to-docx.js``` converts a PDF file to a DOCX file.

```$xslt
node src/exportpdf/export-pdf-to-docx.js
```

#### Export a PDF file to a DOCX file (apply OCR on the PDF file)

The sample script ```export-pdf-to-docx-with-ocr-options.js``` converts a PDF file to a DOCX file. OCR processing is also performed on the input PDF file to extract text from images in the document.

```$xslt
node src/exportpdf/export-pdf-to-docx-with-ocr-options.js
```

#### Export a PDF File To an Image Format (JPEG)

The sample script ```export-pdf-to-jpeg.js``` converts a PDF file's pages to a list of JPEG images.

```$xslt
node src/exportpdftoimages/export-pdf-to-jpeg.js
```

#### Export a PDF File To a Zip of Images (JPEG)

The sample script ```export-pdf-to-jpeg-zip.js``` converts a PDF file's pages to JPEG images. The resulting file is a ZIP archive containing one image per page of the source PDF file.

```$xslt
node src/exportpdftoimages/export-pdf-to-jpeg-zip.js
```

### Combine PDF Files
These samples illustrate how to combine multiple PDF files into a single PDF file.

#### Combine Multiple PDF Files

The sample script ```combine-pdf.js``` combines multiple PDF files into a single PDF file. The combined PDF file contains all pages
of the source files.

```$xslt
node src/combinepdf/combine-pdf.js
```

#### Combine Specific Pages of Multiple PDF Files

The sample script ```combine-pdf-with-page-ranges.js``` combines specific pages of multiple PDF files into into a single PDF file.

```$xslt
node src/combinepdf/combine-pdf-with-page-ranges.js
```

### OCR PDF File
These samples illustrate how to apply OCR(Optical Character Recognition) to a PDF file and convert it to a searchable copy of your PDF.
The supported input format is application/pdf.

#### Convert a PDF File into a Searchable PDF File

The sample script ```ocr-pdf.js``` converts a PDF file into a searchable PDF file.

```$xslt
node src/ocr/ocr-pdf.js
```

#### Convert a PDF File into a Searchable PDF File while keeping the original image

The sample script ```ocr-pdf-with-options.js``` converts a PDF file to a searchable PDF file with maximum fidelity to the original image and default en-us locale. Refer to the documentation of ocr-options.js
to see the list of supported OCR locales and OCR types.

```$xslt
node src/ocr/ocr-pdf-with-options.js
```

### Compress PDF File

The sample illustrates how to reduce the size of a PDF file.

#### Reduce PDF File Size

The sample script ```compress-pdf.js``` reduces the size of a PDF file.

```$xslt
node src/compresspdf/compress-pdf.js
```

#### Reduce PDF File Size on the basis of Compression Level

The sample script ```compress-pdf-with-options.js``` reduces the size of a PDF file on the basis of provided compression level.
Refer to the documentation of compress-pdf-options.js to see the list of supported compression levels.

```$xslt
node src/compresspdf/compress-pdf-with-options.js
```

### Linearize PDF File

The sample illustrates how to convert a PDF file into a Linearized (also known as "web optimized") PDF file. Such PDF files are
optimized for incremental access in network environments.

#### Convert a PDF File into a Web Optimized File

The sample script ```linearize-pdf.js``` optimizes the PDF file for a faster Web View.

```$xslt
node src/linearizepdf/linearize-pdf.js
```

### Protect PDF File

These samples illustrate how to secure a PDF file with a password.

#### Convert a PDF File into a Password Protected PDF File

The sample script ```protect-pdf.js``` converts a PDF file into a password protected PDF file.

```$xslt
node src/protectpdf/protect-pdf.js
```

#### Protect a PDF File with an Owner Password and Permissions

The sample script ```protect-pdf-with-owner-password.js``` secures an input PDF file with owner password and allows certain access permissions
such as copying and editing the contents, and printing of the document at low resolution.

```$xslt
node src/protectpdf/protect-pdf-with-owner-password.js
```

### Remove Protection

The sample illustrates how to remove a password security from a PDF document.

#### Remove Protection from a PDF File

The sample script ```remove-protection.js``` removes a password security from a secured PDF document.

```$xslt
node src/removeprotection/remove-protection.js
```

### Rotate Pages

The sample illustrates how to rotate pages in a PDF file.

#### Rotate Pages in PDF File

The sample script ```rotate-pdf-pages.js``` rotates specific pages in a PDF file.

```$xslt
node src/rotatepages/rotate-pdf-pages.js
```

### Delete Pages

The sample illustrates how to delete pages in a PDF file.

#### Delete Pages from PDF File

The sample script ```delete-pdf-pages.js``` removes specific pages from a PDF file.

```$xslt
node src/deletepages/delete-pdf-pages.js
```

### Reorder Pages

The sample illustrates how to reorder the pages in a PDF file.

#### Reorder Pages in PDF File

The sample script ```reorder-pdf-pages.js``` rearranges the pages of a PDF file according to the specified order.

```$xslt
node src/reorderpages/reorder-pdf-pages.js
```

### Insert Pages

The sample illustrates how to insert pages in a PDF file.

#### Insert Pages into a PDF File

The sample script ```insert-pdf-pages.js``` inserts pages of multiple PDF files into a base PDF file.

```$xslt
node src/insertpages/insert-pdf-pages.js
```

### Replace Pages

The sample illustrates how to replace pages of a PDF file.

#### Replace PDF File Pages with Multiple PDF Files

The sample script ```replace-pdf-pages.js``` replaces specific pages in a PDF file with pages from multiple PDF files.

```$xslt
node src/replacepages/replace-pdf-pages.js
```

### Split PDF File

These samples illustrate how to split PDF file into multiple PDF files.

#### Split PDF By Number of Pages

The sample script ```split-pdf-by-number-of-pages.js``` splits input PDF into multiple PDF files on the basis of the maximum number
of pages each of the output files can have.

```$xslt
node src/splitpdf/split-pdf-by-number-of-pages.js
```

#### Split PDF Into Number of PDF Files

The sample script ```split-pdf-into-number-of-files.js``` splits input PDF into multiple PDF files on the basis of the number
of documents.

```$xslt
node src/splitpdf/split-pdf-into-number-of-files.js
```

#### Split PDF By Page Ranges

The sample script ```split-pdf-by-page-ranges.js``` splits input PDF into multiple PDF files on the basis of page ranges.
Each page range corresponds to a single output file having the pages specified in the page range.

```$xslt
node src/splitpdf/split-pdf-by-page-ranges.js
```

### Document Merge
Adobe Document Merge Operation allows you to produce high fidelity PDF and Word documents with dynamic data inputs.
Using this operation, you can merge your JSON data with Word templates to create dynamic documents for
contracts and agreements, invoices, proposals, reports, forms, branded marketing documents and more.
To know more about document generation and document templates, please checkout the [documentation](http://www.adobe.com/go/dcdocgen_overview_doc)

#### Merge Document to DOCX

The sample script ```merge-document-to-docx.js``` merges the Word based document template with the input JSON data to generate
the output document in the DOCX format

```$xslt
node src/documentmerge/merge-document-to-docx.js
```

#### Merge Document to PDF

This sample script  ```merge-document-to-pdf.js``` merges the Word based document template with the input JSON data to generate
the output document in the PDF format.

```$xslt
node src/documentmerge/merge-document-to-pdf.js
```

#### Merge Document to DOCX with Fragments

This sample script  ```merge-document-to-docx-fragments.js``` merges the Word based document template with the input JSON data and Fragments JSON to generate
the output document in the PDF format.

```$xslt
node src/documentmerge/merge-document-to-docx-fragments.js
```

### PDF Electronic Seal

These samples illustrate how to perform electronic seal over PDF documents like
agreements, invoices, proposals, reports, forms, branded marketing documents and more.
To know more about PDF Electronic Seal, please see the [documentation](https://www.adobe.com/go/dc_eseal_overview_doc).
The following details needs to updated while executing these samples: PROVIDER_NAME, ACCESS_TOKEN, CREDENTIAL_ID and PIN.

#### Apply Electronic Seal

This sample script  ```electronic-seal.js``` uses the sealing options with default appearance options to apply electronic seal over the PDF document.

```$xslt
node src/electronicseal/electronic-seal.js
```

#### Apply Electronic Seal With Custom Appearance Options

This sample script  ```electronic-seal-with-appearance-options.js``` uses the sealing options with custom appearance options to apply electronic seal over the PDF document.

```$xslt
node src/electronicseal/electronic-seal-with-appearance-options.js
```

#### Apply Electronic Seal With Trusted Timestamp

The sample script ```electronic-seal-with-stamp-authority.js``` uses a time stamp authority to apply electronic seal
with trusted timestamp over the PDF document.

```$xslt
node src/electronicseal/electronic-seal-with-stamp-authority.js
```

### Extract PDF

These samples illustrate extracting content of PDF in a structured JSON format along with the renditions inside PDF.
The output of SDK extract operation is Zip package. The Zip package consists of following:

* The structuredData.json file with the extracted content & PDF element structure. See the [JSON schema](https://opensource.adobe.com/pdftools-sdk-docs/release/shared/extractJSONOutputSchema.json). Please refer the [Styling JSON schema](https://opensource.adobe.com/pdftools-sdk-docs/release/shared/extractJSONOutputSchemaStylingInfo.json) for a description of the output when the styling option is enabled.
* A renditions folder(s) containing renditions for each element type selected as input.
  The folder name is either “tables” or “figures” depending on your specified element type.
  Each folder contains renditions with filenames that correspond to the element information in the JSON file.

#### Extract Text Elements

The sample script ```extract-text-info-from-pdf.js``` extracts text elements from PDF document.

```$xslt
node src/extractpdf/extract-text-info-from-pdf.js
```

#### Extract Text, Table Elements

The sample script ```extract-text-table-info-from-pdf.js``` extracts text, table elements from PDF document.

```$xslt
node src/extractpdf/extract-text-table-info-from-pdf.js
```

#### Extract Text, Table Elements with Renditions of Table Elements

The sample script ```extract-text-table-info-with-tables-renditions-from-pdf.js``` extracts text, table elements along with table renditions from PDF document.
Note that the output is a zip containing the structured information along with renditions as described in [section](#extract-pdf).

```$xslt
node src/extractpdf/extract-text-table-info-with-tables-renditions-from-pdf.js
```

#### Extract Text, Table Elements with Renditions of Figure, Table Elements

The sample script ```extract-text-table-info-with-figures-tables-renditions-from-pdf.js``` extracts text, table elements along with figure
and table element's renditions from PDF document. Note that the output is a zip containing the structured information
along with renditions as described in [section](#extract-pdf).

```$xslt
node src/extractpdf/extract-text-table-info-with-figures-tables-renditions-from-pdf.js
```

#### Extract Text Elements and bounding boxes for Characters present in text blocks

The sample script ```extract-text-table-info-with-char-bounds-from-pdf.js``` extracts text elements and bounding boxes
for characters present in text blocks. Note that the output is a zip containing the structured information
along with renditions as described in [section](#extract-pdf).

```$xslt
node src/extractpdf/extract-text-table-info-with-char-bounds-from-pdf.js
```

#### Extract Text, Table Elements and bounding boxes for Characters present in text blocks with Renditions of Table Elements

The sample script ```extract-text-table-info-with-char-bounds-from-pdf.js``` extracts text, table elements, bounding boxes for characters present in text blocks and table element's renditions from PDF document.
Note that the output is a zip containing the structured information along with renditions as described in [section](#extract-pdf).

```$xslt
node src/extractpdf/extract-text-table-info-with-char-bounds-from-pdf.js
```

#### Extract Text, Table Elements with Renditions and CSV's of Table Elements

The sample script ```extract-text-table-info-with-tables-structure-from-pdf.js``` extracts text, table elements, table structures as CSV and table element's renditions from PDF document. Note that the output is a zip containing the structured information along with renditions as described in [section](#extract-pdf).

```$xslt
node src/extractpdf/extract-text-table-info-with-tables-structure-from-pdf.js
```

#### Extract Text, Table Elements with Styling information of text

The sample script ```extract-text-table-info-with-styling-info-from-pdf``` extracts text and table elements along with the styling information of the text blocks. Note that the output is a zip containing the structured information along with renditions as described in [section](#extract-pdf).

```$xslt
node src/extractpdf/extract-text-table-info-with-styling-info-from-pdf.js
```

### PDF Properties

This sample illustrates how to fetch properties of a PDF file.

#### Fetch PDF Properties

The sample script ```get-pdf-properties.js``` fetches the properties of an input PDF.

```$xslt
node src/pdfproperties/get-pdf-properties.js
```

### Custom Client Configuration

These samples illustrate how to provide a custom client configurations(timeouts, proxy etc.).

#### Create a PDF File From a DOCX File (By providing custom value for timeouts)
The sample script ```create-pdf-with-custom-timeouts``` highlights how to provide the custom value for timeout.

```$xslt
node src/customconfigurations/create-pdf-with-custom-timeouts.js
```

#### Create a PDF File From a DOCX File (By providing Proxy Server settings)

The sample script ```create-pdf-with-proxy-server.js``` highlights how to provide Proxy Server configurations to allow
all API calls via that proxy Server.

```$xslt
node src/customconfigurations/create-pdf-with-proxy-server.js
```

#### Create a PDF File From a DOCX File (By providing Proxy Server settings with authentication)

The sample script ```create-pdf-with-authenticated-proxy-server.js``` highlights how to provide Proxy Server
configurations to allow all API calls via that proxy Server that requires authentication.

```$xslt
node src/customconfigurations/create-pdf-with-authenticated-proxy-server.js
```

#### Export a PDF File to a DOCX File (By providing the region)

The sample script ```export-pdf-with-specified-region.js``` highlights how to configure the SDK to process the documents
in the specified region.

```$xslt
node src/customconfigurations/export-pdf-with-specified-region.js
```

### Create Tagged PDF

These samples illustrate how to create a PDF document with enhanced readability from existing PDF document. All tags from the input file will be removed except for existing alt-text images and a
new tagged PDF will be created as output. However, the generated PDF is not guaranteed to comply with accessibility standards such as WCAG and PDF/UA as you may need to perform further downstream remediation to meet those standards.

#### Create Tagged PDF from a PDF

The sample script autotag-pdf highlights how to add tags to PDF document to make the PDF more accessible.

```$xslt
node src/autotag/autotag-pdf.js
```

#### Create Tagged PDF from a PDF along with a report and shift the headings in the output PDF file

The sample script autotag-pdf-with-options highlights how to add tags to PDF documents to make the PDF more accessible and also shift the headings in the output PDF file.
Also, it generates a tagging report which contains the information about the tags that the tagged output PDF document contains.

```$xslt
node src/autotag/autotag-pdf-with-options.js
```

#### Create Tagged PDF from a PDF by setting options with command line arguments

The sample script autotag-pdf-parameterised  highlights how to add tags to PDF documents to make the PDF more accessible by setting options through command line arguments.

Here is a sample list of command line arguments and their description: </br>
--input &lt; input file path &gt; </br>
--output &lt; output file path &gt; </br>
--report { If this argument is present then the output will be generated with the tagging report } </br>
--shift_headings { If this argument is present then the headings will be shifted in the output PDF document } </br>

```$xslt
node src/autotag/autotag-pdf-parameterised.js --report --shift_headings --input resources/autotagPdfInput.pdf --output output/
```

### External Input / Output Storage
These samples illustrate how to use external input and output storage for the supported operations.

####  Create a PDF File From a DOCX File Using External Input Storage

The sample script ```external-input-create-pdf-from-docx.js``` creates a PDF file from a DOCX file stored at external storage.

```$xslt
node src/externalstorage/external-input-create-pdf-from-docx.js
```

####  Create a PDF File From a DOCX File Using External Input Storage and Store the Result in External Output Storage

The sample script ```external-input-and-output-create-pdf-from-docx.js``` creates a PDF file from a DOCX file stored at
external storage and stores the result in external output storage.

```$xslt
node src/externalstorage/external-input-and-output-create-pdf-from-docx.js
```

### Licensing

This project is licensed under the MIT License. See [LICENSE](LICENSE.md) for more information.
#   a d o b e  
 