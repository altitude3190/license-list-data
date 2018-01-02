# License List Data

This repository contains various generated data formats for the [SPDX License List](http://spdx.org/licenses/) including RDFa, HTML, Text, and JSON. The source of the license list which generates these data files can be found at https://github.com/spdx/license-list-XML.  Please note that the format for the license-list-XML repository is internal to the SPDX legal team and is subject to change.

See the file accessingLicenses.md for a description on how to programmatically access the SPDX license list.

The following directories contain the license list in the format specified:

* `html` - Simple HTML format of the files. (*Note:* These pages are not complete and valid HTML files, but simply HTML snippets for the license text.)
* `json` - JSON format for the license list.
* `rdfa` - RDFa/HTML format for the license list.
* `rdfnt` - RDF NT format for the license list.
* `rdfturtle` - RDF turtle format for the license list.
* `rdfxml` - RDF/XML format for the license list.
* `template` - SPDX template files per the license templates specified in the SPDX 2.0 specification appendix.  Deprecated licenses start with "deprecated_".
* `text` - Simple text files.  Deprecated licenses start with "deprecated_".
* `website` - HTML generated for the http://spdx.org/ website.

The file licenses.md is a table of contents for the generated licenses.  The links for the files point to the text for the license.

Technical questions or issues can be sent to the [SPDX technical team mailing list](mailto:spdx-tech@lists.spdx.org).
Questions or issues on the license content can be sent to the [SPDX legal team mailing list](mailto:spdx-legal@lists.spdx.org).

Note that the content of this repository is generated by the [SPDX tools](http://github.com/spdx/tools) from the [license list source](https://github.com/spdx/license-list-XML).

As far as the *content* of the license information is concerned, any [issues](https://github.com/spdx/license-list-XML/issues) or [pull requests](https://github.com/spdx/license-list-XML/pulls) should be logged at the [license list source](https://github.com/spdx/license-list-XML) project.

As far as the output *format* or the *generation* of the output files is concerned, any [issues](https://github.com/spdx/tools/issues) or [pull requests](https://github.com/spdx/tools/pulls) should be logged at the [SPDX tools](http://github.com/spdx/tools) project.

## License List Data Build Process
The license list data in this repository is automatically built on commits to the master branch of the [license list source](https://github.com/spdx/license-list-XML) by the [Travis-ci script](https://github.com/spdx/license-list-XML/blob/master/.travis.yml).  The commit message generated by the script includes short form of the commit hash from the license list source.  If the license list source has been tagged for release, a tag will also be generated for the license-list-data repository.

The script that publishes the license list data can be found in the .travis directory in the license list source.

The script uses the SPDX tools LicenseRDFaGenerator command to generate the data files.

Source code for the LicenseRDFaGenerator can be found in the [SPDX tools](http://github.com/spdx/tools) repository.  

The main entrypoint for the command is [LicenseRDFaGenerator.java](https://github.com/spdx/tools/blob/4c9054942fd8ba1fb691de8950aeeca3fdf4addf/src/org/spdx/tools/LicenseRDFAGenerator.java#L121)

he basic flow of the program is LicenseRDFaGenerator -> Translate XML to the license objects (including the license text) -> Translate the license into various output files (including the text and template files).

The code that translates the license XML into the license template text is [LicenseXmlHelper.getLicenseTemplate](https://github.com/spdx/tools/blob/4c9054942fd8ba1fb691de8950aeeca3fdf4addf/src/org/spdx/licensexml/LicenseXmlHelper.java#L498) and the code that translates the license XML into text is [LicenseXmlHelper.getLicenseText](https://github.com/spdx/tools/blob/4c9054942fd8ba1fb691de8950aeeca3fdf4addf/src/org/spdx/licensexml/LicenseXmlHelper.java#L523.