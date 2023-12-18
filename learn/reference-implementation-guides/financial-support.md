# Financial Support

### Usecase

A provider platform which acts as BPP provides scholarships and a seeker platform which acts as BAP will help the people to avail scholarships through its platform.

### Flow Diagram

<figure><img src="../../.gitbook/assets/financial-support-flow.jpeg" alt=""><figcaption></figcaption></figure>

### API Mapping and Sample JSON's

1. BAP will make search request with an intent like scholarship name, gender etc.

#### Search API (**Search by gender)**

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-022723112309",
        "message_id": "a9aaecca-10b7-4d19-b640-b047a7c60009",
        "timestamp": "2023-02-06T09:55:41.161Z",
        "ttl": "PT10M"
    },
    "message": {
        "intent": {
            "fulfillment": {
                "customer": {
                    "person": {
                        "gender": "Female"
                    }
                }
            }
        }
    }
}
```

#### **Search API (Search by Scholarship Name)**

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-022723112309",
        "message_id": "a9aaecca-10b7-4d19-b640-b047a7c60009",
        "timestamp": "2023-02-06T09:55:41.161Z",
        "ttl": "PT10M"
    },
   "message": {
      "intent": {
         "item": {
            "descriptor": {
               "name": "scholarship for undergraduate"
            }
         }
      }
   }
}
```

#### **Search API (Search by Gender and Scholarship Name)**

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-022723112309",
        "message_id": "a9aaecca-10b7-4d19-b640-b047a7c60009",
        "timestamp": "2023-02-06T09:55:41.161Z",
        "ttl": "PT10M"
    },
   "message": {
      "intent": {
         "item": {
            "descriptor": {
               "name": "scholarship for undergraduate"
            }
         },
         "fulfillment": {
            "customer": {
               "person": {
                  "gender": "Female"
               }
            }
         }
      }
   }
}
```

2. BPP will create a catalogue of scholarships with matching criteria and sends it in on\_search request.

#### On Search API

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "on_search",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
   "message": {
      "catalog": {
         "descriptor": {
            "name": "Protean DSEP Scholarships and Grants BPP Platform"
         },
         "providers": [
            {
               "id": "BX213573733",
               "descriptor": {
                  "name": "XYZ Education Foundation",
                  "short_desc" : "Short Description about the Foundation",
                  "images": [
                     {
                        "url" : "url of the image of the provider"
                     }
                  ]
               },
               "categories": [
                  {
                     "id": "DSEP_CAT_1",
                     "descriptor": {
                        "code": "ug",
                        "name": "Under Graduate"
                     }
                  }
               ],
               "fulfillments": [
                  {
                     "id": "DSEP_FUL_63587501",
                     "type": "SCHOLARSHIP",
                     "tracking": false,
                     "contact": {
                        "phone": "9876543210",
                        "email": "maryg@xyz.com"
                     },
                     "stops": [
                        {
                           "type": "APPLICATION-START",
                           "time": {
                              "timestamp": "2022-09-01T00:00:00.000Z"
                           }
                        },
                        {
                           "type": "APPLICATION-END",
                           "time": {
                              "timestamp": "2022-10-31T00:00:00.000Z"
                           }
                        }
                     ]
                  }
               ],
               "items": [
                  {
                     "id": "SCM_63587501",
                     "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                     },
                     "price": {
                        "currency": "INR",
                        "value": "Upto RS.1000 per year"
                     },
                     "rateable": false,
                     "tags": [
                        {
                           "display": true,
                           "descriptor": {
                              "code": "benefits",
                              "name": "Benefits"
                           },
                           "list": [
                              {
                                 "descriptor": {
                                    "code": "scholarship-amount",
                                    "name": "Scholarship Amount"
                                 },
                                 "value": "Upto Rs.25000 per year",
                                 "display": true
                              }
                           ]
                        }
                     ],
                     "category_ids": ["DSEP_CAT_1"],
                     "fulfillment_ids": ["DSEP_FUL_63587501"]
                  }
               ],
               "rateable": false
            }
         ]
      }
   }
}
```

3. BAP will send the init request with basic custom details to initialize the scholarship application process.

#### Init API

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "init",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
   "message": {
      "order": {
         "items": [
            {
               "id": "SCM_63587501"
            }
         ],
         "provider": {
            "id": "BX213573733"
         },
         "billing": {
            "name": "Manjunath",
            "organization": {
               "descriptor": {
                  "name": "Namma Yatri",
                  "code": "nammayatri.in"
               },
               "contact": {
                  "phone": "+91-8888888888",
                  "email": "scholarships@nammayatri.in"
               }
            },
            "address": "No 27, XYZ Lane, etc",
            "phone": "+91-9999999999"
         },
         "fulfillments": [
            {
               "customer": {
                  "id": "aadhaar:798677675565",
                  "person": {
                     "name": "Jane Doe",
                     "age": "13",
                     "gender": "female"
                  },
                  "contact": {
                     "phone": "+91-9663088848",
                     "email": "jane.doe@example.com"
                  }
               }
            }
         ],
         "payments" : [
            {
               "params" :{
                  "bank_code": "IFSC_Code_Of_the_bank",
                  "bank_account_number" :"121212121212",
                  "bank_account_name" : "Account Holder Name"
               }

            }
         ]

      }
   }
}
```

4. BPP will send the on\_init with xinput form URL to collect the complete user details.

#### On Init API (Step-1)

If BPP has multiple forms to collect the data, he will make on\_init request with the form number(current index) and total number of forms(max index).\
\
BPP should generate the xinput form with transaction id(request.context.transaction\_id). So that the forms can be tagged with a lifecyle.

BAP should render the xinput form on the UI and collect all the details. &#x20;

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "on_init",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
   "message": {
      "order": {
         "provider": {
            "id": "471",
            "descriptor": {
               "name": "XYZ Education Foundation",
               "short_desc" : "Short Description about the Foundation",
               "images": [
                  {
                     "url" : "url of the image of the provider"
                  }
               ]
            },
            "rateable": false
         },
         "items": [
            {
               "id": "SCM_63587501",
               "descriptor": {
                  "name": "XYZ Education Scholarship for Undergraduate Students",
                  "long_desc": "XYZ Education Scholarship for Undergraduate Students"
               },
               "price": {
                  "currency": "INR",
                  "value": "Upto RS.1000 per year"
               },
               "xinput": {
                  "required": true,
                  "head": {
                     "descriptor": {
                        "name": "Application Form"
                     },
                     "index": {
                        "min": 0,
                        "cur": 0,
                        "max": 3
                     },
                     "headings": [
                        "Personal Details",
                        "Educational Details",
                        "Financial Information",
                        "Review & Submit"
                     ]
                  },
                  "form": {
                     "mime_type": "text/html",
                     "url": "https://6vs8xnx5i7.vidyasaarathi.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f",
                     "resubmit": false,
                     "auth": {
                        "descriptor": {
                           "code": "jwt"
                        },
                        "value": "eyJhbGciOiJIUzI.eyJzdWIiOiIxMjM0NTY3O.SflKxwRJSMeKKF2QT4"
                     }
                  }
               },
               "rateable": false,
               "tags": [
                  {
                     "display": true,
                     "descriptor": {
                        "code": "eligibility-criteria",
                        "name": "Eligibility Criteria"
                     },
                     "list": [
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "SC",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "ST",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "OB",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "NT",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "gender_criteria",
                              "name": "Gender Criteria"
                           },
                           "value": "ALL",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Thane",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Nagpur",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Yavatmal",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Ahmed Nagar",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Solapur",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Pune",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "state_criteria",
                              "name": "State Criteria"
                           },
                           "value": "MAHARASHTRA",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "qualification_criteria",
                              "name": "Qualification Criteria"
                           },
                           "value": "Class 10|Min. score=50|Max. score=null",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "qualification_criteria",
                              "name": "Qualification Criteria"
                           },
                           "value": "Class 12|Min. score=60|Max. score=null",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "financial_income_criteria",
                              "name": "Financial Income Criteria"
                           },
                           "value": "Max Family Income - Rs.500000.00",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "financial_year",
                              "name": "Financial Year"
                           },
                           "value": "2023-2024",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "certificate_instructions",
                              "name": "Certificate Instructions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        }
                     ]
                  },
                  {
                     "display": true,
                     "descriptor": {
                        "code": "additional_info",
                        "name": "Additional Info"
                     },
                     "list": [
                        {
                           "descriptor": {
                              "code": "faq",
                              "name": "Frequently Asked Questions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "terms_conditions",
                              "name": "Terms and Conditions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        }
                     ]
                  }
               ],
               "fulfillment_ids": [
                  "VSP_FUL_1113"
               ]
            }
         ],
         "billing": {
            "name": "Manjunath",
            "organization": {
               "descriptor": {
                  "name": "Namma Yatri",
                  "code": "nammayatri.in"
               },
               "contact": {
                  "phone": "+91-8888888888",
                  "email": "scholarships@nammayatri.in"
               }
            },
            "address": "No 27, XYZ Lane, etc",
            "phone": "+91-9999999999"
         },
         "fulfillments": [
            {
               "state" : {
                  "descriptor" : {
                     "code": "APPLICATION-STARTED",
                     "name" : "Application started"
                  },
                  "updated_at" : "2023-02-06T09:55:41.161Z"
               },
               "id": "VSP_FUL_1113",
               "type": "SCHOLARSHIP",
               "tracking": false,
               "agent" : {
                  "person" : {
                     "name" : "Ekstep Foundation SPoc"
                  },
                  "contact" : {
                     "email" : "ekstepsupport@ekstep.com"
                  }
               },
               "customer": {
                  "id": "aadhaar:798677675565",
                  "person": {
                     "name": "Jane Doe",
                     "age": "13",
                     "gender": "female"
                  },
                  "contact": {
                     "phone": "+91-9663088848",
                     "email": "jane.doe@example.com"
                  }
               },
               "stops": [
                  {
                     "type": "APPLICATION-START",
                     "time": {
                        "timestamp": "2023-07-14T18:30:00.000Z"
                     }
                  },
                  {
                     "type": "APPLICATION-END",
                     "time": {
                        "timestamp": "2025-07-13T18:30:00.000Z"
                     }
                  }
               ]
            }
         ],
         "payments" : [
            {
               "params" :{
                  "bank_code": "IFSC_Code_Of_the_bank",
                  "bank_account_number" :"121212121212",
                  "bank_account_name" : "Account Holder Name"
               }

            }
         ],
         "quote" :{
            "price" : {
               "currency" : "INR",
               "value" : "250000"
            },
            "breakup":[
               {
                  "title": "Tution fee",
                  "price" : {
                     "currency" : "INR",
                     "value" : "150000"
                  }
               },
               {
                  "title": "Hostel fee",
                  "price" : {
                     "currency" : "INR",
                     "value" : "50000"
                  }
               },
               {
                  "title": "Books",
                  "price" : {
                     "currency" : "INR",
                     "value" : "50000"
                  }
               }
            ]
         }
      }
   }
}
```

#### On Init API (Step-2)

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "on_init",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc" : "Short Description about the Foundation",
                    "images": [
                        {
                            "url" : "url of the image of the provider"
                        }
                    ]
                },
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "Upto RS.1000 per year"
                    },
                    "xinput": {
                        "required": true,
                        "head": {
                            "descriptor": {
                                "name": "Application Form"
                            },
                            "index": {
                                "min": 0,
                                "cur": 1,
                                "max": 3
                            },
                            "headings": [
                                "Personal Details",
                                "Educational Details",
                                "Financial Information",
                                "Review & Submit"
                            ]
                        },
                        "form": {
                            "mime_type": "text/html",
                            "url": "https://6vs8xnx5i7.vidyasaarathi.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f",
                            "resubmit": false,
                            "auth": {
                                "descriptor": {
                                    "code": "jwt"
                                },
                                "value": "eyJhbGciOiJIUzI.eyJzdWIiOiIxMjM0NTY3O.SflKxwRJSMeKKF2QT4"
                            }
                        }
                    },
                    "rateable": false,
                    "tags": [
                        {
                            "display": true,
                            "descriptor": {
                                "code": "eligibility-criteria",
                                "name": "Eligibility Criteria"
                            },
                            "list": [
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "SC",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "ST",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "OB",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "NT",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "gender_criteria",
                                        "name": "Gender Criteria"
                                    },
                                    "value": "ALL",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Thane",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Nagpur",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Yavatmal",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Ahmed Nagar",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Solapur",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Pune",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "state_criteria",
                                        "name": "State Criteria"
                                    },
                                    "value": "MAHARASHTRA",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "qualification_criteria",
                                        "name": "Qualification Criteria"
                                    },
                                    "value": "Class 10|Min. score=50|Max. score=null",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "qualification_criteria",
                                        "name": "Qualification Criteria"
                                    },
                                    "value": "Class 12|Min. score=60|Max. score=null",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "financial_income_criteria",
                                        "name": "Financial Income Criteria"
                                    },
                                    "value": "Max Family Income - Rs.500000.00",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "financial_year",
                                        "name": "Financial Year"
                                    },
                                    "value": "2023-2024",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "certificate_instructions",
                                        "name": "Certificate Instructions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                }
                            ]
                        },
                        {
                            "display": true,
                            "descriptor": {
                                "code": "additional_info",
                                "name": "Additional Info"
                            },
                            "list": [
                                {
                                    "descriptor": {
                                        "code": "faq",
                                        "name": "Frequently Asked Questions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "terms_conditions",
                                        "name": "Terms and Conditions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                }
                            ]
                        }
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state" : {
                        "descriptor" : {
                            "code": "APPLICATION-STARTED",
                            "name" : "Application started"
                        },
                        "updated_at" : "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "type": "SCHOLARSHIP",
                    "tracking": false,
                    "agent" : {
                        "person" : {
                            "name" : "Ekstep Foundation SPoc"
                        },
                        "contact" : {
                            "email" : "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    },
                    "stops": [
                        {
                            "type": "APPLICATION-START",
                            "time": {
                                "timestamp": "2023-07-14T18:30:00.000Z"
                            }
                        },
                        {
                            "type": "APPLICATION-END",
                            "time": {
                                "timestamp": "2025-07-13T18:30:00.000Z"
                            }
                        }
                    ]
                }
            ],
            "payments" : [
                {
                    "params" :{
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number" :"121212121212",
                        "bank_account_name" : "Account Holder Name"
                    }

                }
            ],
            "quote" :{
                "price" : {
                    "currency" : "INR",
                    "value" : "250000"
                },
                "breakup":[
                    {
                        "title": "Tution fee",
                        "price" : {
                            "currency" : "INR",
                            "value" : "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price" : {
                            "currency" : "INR",
                            "value" : "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price" : {
                            "currency" : "INR",
                            "value" : "50000"
                        }
                    }
                ]
            } 
        }
    }
}
```

**On Init API (Step-3)**

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "on_init",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc" : "Short Description about the Foundation",
                    "images": [
                        {
                            "url" : "url of the image of the provider"
                        }
                    ]
                },
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "Upto RS.1000 per year"
                    },
                    "xinput": {
                        "required": true,
                        "head": {
                            "descriptor": {
                                "name": "Application Form"
                            },
                            "index": {
                                "min": 0,
                                "cur": 2,
                                "max": 3
                            },
                            "headings": [
                                "Personal Details",
                                "Educational Details",
                                "Financial Information",
                                "Review & Submit"
                            ]
                        },
                        "form": {
                            "mime_type": "text/html",
                            "url": "https://6vs8xnx5i7.vidyasaarathi.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f",
                            "resubmit": false,
                            "auth": {
                                "descriptor": {
                                    "code": "jwt"
                                },
                                "value": "eyJhbGciOiJIUzI.eyJzdWIiOiIxMjM0NTY3O.SflKxwRJSMeKKF2QT4"
                            }
                        }
                    },
                    "rateable": false,
                    "tags": [
                        {
                            "display": true,
                            "descriptor": {
                                "code": "eligibility-criteria",
                                "name": "Eligibility Criteria"
                            },
                            "list": [
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "SC",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "ST",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "OB",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "NT",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "gender_criteria",
                                        "name": "Gender Criteria"
                                    },
                                    "value": "ALL",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Thane",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Nagpur",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Yavatmal",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Ahmed Nagar",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Solapur",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Pune",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "state_criteria",
                                        "name": "State Criteria"
                                    },
                                    "value": "MAHARASHTRA",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "qualification_criteria",
                                        "name": "Qualification Criteria"
                                    },
                                    "value": "Class 10|Min. score=50|Max. score=null",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "qualification_criteria",
                                        "name": "Qualification Criteria"
                                    },
                                    "value": "Class 12|Min. score=60|Max. score=null",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "financial_income_criteria",
                                        "name": "Financial Income Criteria"
                                    },
                                    "value": "Max Family Income - Rs.500000.00",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "financial_year",
                                        "name": "Financial Year"
                                    },
                                    "value": "2023-2024",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "certificate_instructions",
                                        "name": "Certificate Instructions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                }
                            ]
                        },
                        {
                            "display": true,
                            "descriptor": {
                                "code": "additional_info",
                                "name": "Additional Info"
                            },
                            "list": [
                                {
                                    "descriptor": {
                                        "code": "faq",
                                        "name": "Frequently Asked Questions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "terms_conditions",
                                        "name": "Terms and Conditions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                }
                            ]
                        }
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state" : {
                        "descriptor" : {
                            "code": "APPLICATION-STARTED",
                            "name" : "Application started"
                        },
                        "updated_at" : "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "type": "SCHOLARSHIP",
                    "tracking": false,
                    "agent" : {
                        "person" : {
                            "name" : "Ekstep Foundation SPoc"
                        },
                        "contact" : {
                            "email" : "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    },
                    "stops": [
                        {
                            "type": "APPLICATION-START",
                            "time": {
                                "timestamp": "2023-07-14T18:30:00.000Z"
                            }
                        },
                        {
                            "type": "APPLICATION-END",
                            "time": {
                                "timestamp": "2025-07-13T18:30:00.000Z"
                            }
                        }
                    ]
                }
            ],
            "payments" : [
                {
                    "params" :{
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number" :"121212121212",
                        "bank_account_name" : "Account Holder Name"
                    }

                }
            ],
            "quote" :{
                "price" : {
                    "currency" : "INR",
                    "value" : "250000"
                },
                "breakup":[
                    {
                        "title": "Tution fee",
                        "price" : {
                            "currency" : "INR",
                            "value" : "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price" : {
                            "currency" : "INR",
                            "value" : "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price" : {
                            "currency" : "INR",
                            "value" : "50000"
                        }
                    }
                ]
            } 
        }
    }
}
```

#### On Init API (Step-4)

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "on_init",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc" : "Short Description about the Foundation",
                    "images": [
                        {
                            "url" : "url of the image of the provider"
                        }
                    ]
                },
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "Upto RS.1000 per year"
                    },
                    "xinput": {
                        "required": true,
                        "head": {
                            "descriptor": {
                                "name": "Application Form"
                            },
                            "index": {
                                "min": 0,
                                "cur": 3,
                                "max": 3
                            },
                            "headings": [
                                "Personal Details",
                                "Educational Details",
                                "Financial Information",
                                "Review & Submit"
                            ]
                        },
                        "form": {
                            "mime_type": "text/html",
                            "url": "https://6vs8xnx5i7.vidyasaarathi.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f",
                            "resubmit": false,
                            "auth": {
                                "descriptor": {
                                    "code": "jwt"
                                },
                                "value": "eyJhbGciOiJIUzI.eyJzdWIiOiIxMjM0NTY3O.SflKxwRJSMeKKF2QT4"
                            }
                        }
                    },
                    "rateable": false,
                    "tags": [
                        {
                            "display": true,
                            "descriptor": {
                                "code": "eligibility-criteria",
                                "name": "Eligibility Criteria"
                            },
                            "list": [
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "SC",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "ST",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "OB",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "NT",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "gender_criteria",
                                        "name": "Gender Criteria"
                                    },
                                    "value": "ALL",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Thane",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Nagpur",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Yavatmal",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Ahmed Nagar",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Solapur",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Pune",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "state_criteria",
                                        "name": "State Criteria"
                                    },
                                    "value": "MAHARASHTRA",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "qualification_criteria",
                                        "name": "Qualification Criteria"
                                    },
                                    "value": "Class 10|Min. score=50|Max. score=null",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "qualification_criteria",
                                        "name": "Qualification Criteria"
                                    },
                                    "value": "Class 12|Min. score=60|Max. score=null",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "financial_income_criteria",
                                        "name": "Financial Income Criteria"
                                    },
                                    "value": "Max Family Income - Rs.500000.00",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "financial_year",
                                        "name": "Financial Year"
                                    },
                                    "value": "2023-2024",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "certificate_instructions",
                                        "name": "Certificate Instructions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                }
                            ]
                        },
                        {
                            "display": true,
                            "descriptor": {
                                "code": "additional_info",
                                "name": "Additional Info"
                            },
                            "list": [
                                {
                                    "descriptor": {
                                        "code": "faq",
                                        "name": "Frequently Asked Questions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "terms_conditions",
                                        "name": "Terms and Conditions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                }
                            ]
                        }
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state" : {
                        "descriptor" : {
                            "code": "APPLICATION-STARTED",
                            "name" : "Application started"
                        },
                        "updated_at" : "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "type": "SCHOLARSHIP",
                    "tracking": false,
                    "agent" : {
                        "person" : {
                            "name" : "Ekstep Foundation SPoc"
                        },
                        "contact" : {
                            "email" : "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    },
                    "stops": [
                        {
                            "type": "APPLICATION-START",
                            "time": {
                                "timestamp": "2023-07-14T18:30:00.000Z"
                            }
                        },
                        {
                            "type": "APPLICATION-END",
                            "time": {
                                "timestamp": "2025-07-13T18:30:00.000Z"
                            }
                        }
                    ]
                }
            ],
            "payments" : [
                {
                    "params" :{
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number" :"121212121212",
                        "bank_account_name" : "Account Holder Name"
                    }

                }
            ],
            "quote" :{
                "price" : {
                    "currency" : "INR",
                    "value" : "250000"
                },
                "breakup":[
                    {
                        "title": "Tution fee",
                        "price" : {
                            "currency" : "INR",
                            "value" : "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price" : {
                            "currency" : "INR",
                            "value" : "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price" : {
                            "currency" : "INR",
                            "value" : "50000"
                        }
                    }
                ]
            } 
        }
    }
}
```

#### On Init API (Step-5)

If there are no more forms to be filled, BPP will send on\_init request without xinput form details.

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "on_init",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc" : "Short Description about the Foundation",
                    "images": [
                        {
                            "url" : "url of the image of the provider"
                        }
                    ]
                },
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "Upto RS.1000 per year"
                    },
                    "rateable": false,
                    "tags": [
                        {
                            "display": true,
                            "descriptor": {
                                "code": "eligibility-criteria",
                                "name": "Eligibility Criteria"
                            },
                            "list": [
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "SC",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "ST",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "OB",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "course_category_criteria",
                                        "name": "Course Category Criteria"
                                    },
                                    "value": "NT",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "gender_criteria",
                                        "name": "Gender Criteria"
                                    },
                                    "value": "ALL",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Thane",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Nagpur",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Yavatmal",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Ahmed Nagar",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Solapur",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "city_criteria",
                                        "name": "City Criteria"
                                    },
                                    "value": "Pune",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "state_criteria",
                                        "name": "State Criteria"
                                    },
                                    "value": "MAHARASHTRA",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "qualification_criteria",
                                        "name": "Qualification Criteria"
                                    },
                                    "value": "Class 10|Min. score=50|Max. score=null",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "qualification_criteria",
                                        "name": "Qualification Criteria"
                                    },
                                    "value": "Class 12|Min. score=60|Max. score=null",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "financial_income_criteria",
                                        "name": "Financial Income Criteria"
                                    },
                                    "value": "Max Family Income - Rs.500000.00",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "financial_year",
                                        "name": "Financial Year"
                                    },
                                    "value": "2023-2024",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "certificate_instructions",
                                        "name": "Certificate Instructions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                }
                            ]
                        },
                        {
                            "display": true,
                            "descriptor": {
                                "code": "additional_info",
                                "name": "Additional Info"
                            },
                            "list": [
                                {
                                    "descriptor": {
                                        "code": "faq",
                                        "name": "Frequently Asked Questions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                },
                                {
                                    "descriptor": {
                                        "code": "terms_conditions",
                                        "name": "Terms and Conditions"
                                    },
                                    "value": "ZMT Education 15JUL23",
                                    "display": true
                                }
                            ]
                        }
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state" : {
                        "descriptor" : {
                            "code": "APPLICATION-COMPLETED",
                            "name" : "Application Completed"
                        },
                        "updated_at" : "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "type": "SCHOLARSHIP",
                    "tracking": false,
                    "agent" : {
                        "person" : {
                            "name" : "Ekstep Foundation SPoc"
                        },
                        "contact" : {
                            "email" : "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    },
                    "stops": [
                        {
                            "type": "APPLICATION-START",
                            "time": {
                                "timestamp": "2023-07-14T18:30:00.000Z"
                            }
                        },
                        {
                            "type": "APPLICATION-END",
                            "time": {
                                "timestamp": "2025-07-13T18:30:00.000Z"
                            }
                        }
                    ]
                }
            ],
            "cancellation_terms" : [
                {
                    "cancellation_fee" : {
                        "amount" : {
                            "currency" : "INR",
                            "value" : "Penalty upto 5,00,000 INR"
                        }
                    }
                }

            ],
            "payments" : [
                {
                    "params" :{
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number" :"121212121212",
                        "bank_account_name" : "Account Holder Name"
                    }

                }
            ],
            "quote" :{
                "price" : {
                    "currency" : "INR",
                    "value" : "250000"
                },
                "breakup":[
                    {
                        "title": "Tution fee",
                        "price" : {
                            "currency" : "INR",
                            "value" : "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price" : {
                            "currency" : "INR",
                            "value" : "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price" : {
                            "currency" : "INR",
                            "value" : "50000"
                        }
                    }
                ]
            } 
        }
    }
}
```

5. BAP sends confirms request to confirm the scholarship application.

#### Confirm API

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "confirm",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
   "message": {
      "order": {
         "items": [
            {
               "id": "SCM_63587501"
            }
         ],
         "provider": {
            "id": "BX213573733"
         },
         "billing": {
            "name": "Manjunath",
            "organization": {
               "descriptor": {
                  "name": "Namma Yatri",
                  "code": "nammayatri.in"
               },
               "contact": {
                  "phone": "+91-8888888888",
                  "email": "scholarships@nammayatri.in"
               }
            },
            "address": "No 27, XYZ Lane, etc",
            "phone": "+91-9999999999"
         },
         "fulfillments": [
            {
               "customer": {
                  "id": "aadhaar:798677675565",
                  "person": {
                     "name": "Jane Doe",
                     "age": "13",
                     "gender": "female"
                  },
                  "contact": {
                     "phone": "+91-9663088848",
                     "email": "jane.doe@example.com"
                  }
               }
            }
         ],
         "payment" : [
            {
               "params" :{
                  "bank_code": "IFSC_Code_Of_the_bank",
                  "bank_account_number" :"121212121212",
                  "bank_account_name" : "Account Holder Name"
               }
            }
         ]
      }
   }
}
```

6. BPP will send the confirmation of scholarship application.

#### On Confirm API

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "on_confirm",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
   "message": {
      "order": {
         "id": "12424kh",
         "provider": {
            "id": "471",
            "descriptor": {
               "name": "XYZ Education Foundation",
               "short_desc" : "Short Description about the Foundation",
               "images": [
                  {
                     "url" : "url of the image of the provider"
                  }
               ]
            },
            "rateable": false
         },
         "items": [
            {
               "id": "SCM_63587501",
               "descriptor": {
                  "name": "XYZ Education Scholarship for Undergraduate Students",
                  "long_desc": "XYZ Education Scholarship for Undergraduate Students"
               },
               "price": {
                  "currency": "INR",
                  "value": "Upto RS.1000 per year"
               },
               "rateable": false,
               "tags": [
                  {
                     "display": true,
                     "descriptor": {
                        "code": "eligibility-criteria",
                        "name": "Eligibility Criteria"
                     },
                     "list": [
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "SC",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "ST",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "OB",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "NT",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "gender_criteria",
                              "name": "Gender Criteria"
                           },
                           "value": "ALL",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Thane",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Nagpur",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Yavatmal",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Ahmed Nagar",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Solapur",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Pune",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "state_criteria",
                              "name": "State Criteria"
                           },
                           "value": "MAHARASHTRA",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "qualification_criteria",
                              "name": "Qualification Criteria"
                           },
                           "value": "Class 10|Min. score=50|Max. score=null",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "qualification_criteria",
                              "name": "Qualification Criteria"
                           },
                           "value": "Class 12|Min. score=60|Max. score=null",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "financial_income_criteria",
                              "name": "Financial Income Criteria"
                           },
                           "value": "Max Family Income - Rs.500000.00",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "financial_year",
                              "name": "Financial Year"
                           },
                           "value": "2023-2024",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "certificate_instructions",
                              "name": "Certificate Instructions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        }
                     ]
                  },
                  {
                     "display": true,
                     "descriptor": {
                        "code": "additional_info",
                        "name": "Additional Info"
                     },
                     "list": [
                        {
                           "descriptor": {
                              "code": "faq",
                              "name": "Frequently Asked Questions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "terms_conditions",
                              "name": "Terms and Conditions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        }
                     ]
                  }
               ],
               "fulfillment_ids": [
                  "VSP_FUL_1113"
               ]
            }
         ],
         "billing": {
            "name": "Manjunath",
            "organization": {
               "descriptor": {
                  "name": "Namma Yatri",
                  "code": "nammayatri.in"
               },
               "contact": {
                  "phone": "+91-8888888888",
                  "email": "scholarships@nammayatri.in"
               }
            },
            "address": "No 27, XYZ Lane, etc",
            "phone": "+91-9999999999"
         },
         "fulfillments": [
            {
               "state" : {
                  "descriptor" : {
                     "code": "APPLICATION-SUBMITTED",
                     "name" : "Application Submitted"
                  },
                  "updated_at" : "2023-02-06T09:55:41.161Z"
               },
               "id": "VSP_FUL_1113",
               "type": "SCHOLARSHIP",
               "tracking": false,
               "agent" : {
                  "person" : {
                     "name" : "Ekstep Foundation SPoc"
                  },
                  "contact" : {
                     "email" : "ekstepsupport@ekstep.com"
                  }
               },
               "customer": {
                  "id": "aadhaar:798677675565",
                  "person": {
                     "name": "Jane Doe",
                     "age": "13",
                     "gender": "female"
                  },
                  "contact": {
                     "phone": "+91-9663088848",
                     "email": "jane.doe@example.com"
                  }
               },
               "stops": [
                  {
                     "type": "APPLICATION-START",
                     "time": {
                        "timestamp": "2023-07-14T18:30:00.000Z"
                     }
                  },
                  {
                     "type": "APPLICATION-END",
                     "time": {
                        "timestamp": "2025-07-13T18:30:00.000Z"
                     }
                  }
               ]
            }
         ],
         "cancellation_terms" : [
            {
               "cancellation_fee" : {
                  "amount" : {
                     "currency" : "INR",
                     "value" : "Penalty upto 5,00,000 INR"
                  }
               }
            }

         ],
         "docs": [
            {
               "descriptor":{
                  "name" :"Application Details",
                  "short_desc" : "To open this document, enter the password sent to your email mayan****@***.com"
               },
               "url" : "https://link-to-the-document.com",
               "mime_type" : "application/pdf"
            }
         ],
         "payments" : [
            {
               "params" :{
                  "bank_code": "IFSC_Code_Of_the_bank",
                  "bank_account_number" :"121212121212",
                  "bank_account_name" : "Account Holder Name"
               }

            }
         ],
         "quote" :{
            "price" : {
               "currency" : "INR",
               "value" : "250000"
            },
            "breakup":[
               {
                  "title": "Tution fee",
                  "price" : {
                     "currency" : "INR",
                     "value" : "150000"
                  }
               },
               {
                  "title": "Hostel fee",
                  "price" : {
                     "currency" : "INR",
                     "value" : "50000"
                  }
               },
               {
                  "title": "Books",
                  "price" : {
                     "currency" : "INR",
                     "value" : "50000"
                  }
               }
            ]
         }
      }
   }
}
```

7. BAP can use the status API to fetch the scholarship application status.

#### Status API

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "status",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
    "message": {
        "order_id" : "12424kh"
    }
}
```

8. BPP send the on\_status request, with scholarship application status.

#### On Status (Scholarship Approved)

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "on_status",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
   "message": {
      "order": {
         "id": "12424kh",
         "provider": {
            "id": "471",
            "descriptor": {
               "name": "XYZ Education Foundation",
               "short_desc" : "Short Description about the Foundation",
               "images": [
                  {
                     "url" : "url of the image of the provider"
                  }
               ]
            },
            "rateable": false
         },
         "items": [
            {
               "id": "SCM_63587501",
               "descriptor": {
                  "name": "XYZ Education Scholarship for Undergraduate Students",
                  "long_desc": "XYZ Education Scholarship for Undergraduate Students"
               },
               "price": {
                  "currency": "INR",
                  "value": "Upto RS.1000 per year"
               },
               "rateable": false,
               "tags": [
                  {
                     "display": true,
                     "descriptor": {
                        "code": "eligibility-criteria",
                        "name": "Eligibility Criteria"
                     },
                     "list": [
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "SC",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "ST",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "OB",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "NT",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "gender_criteria",
                              "name": "Gender Criteria"
                           },
                           "value": "ALL",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Thane",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Nagpur",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Yavatmal",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Ahmed Nagar",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Solapur",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Pune",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "state_criteria",
                              "name": "State Criteria"
                           },
                           "value": "MAHARASHTRA",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "qualification_criteria",
                              "name": "Qualification Criteria"
                           },
                           "value": "Class 10|Min. score=50|Max. score=null",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "qualification_criteria",
                              "name": "Qualification Criteria"
                           },
                           "value": "Class 12|Min. score=60|Max. score=null",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "financial_income_criteria",
                              "name": "Financial Income Criteria"
                           },
                           "value": "Max Family Income - Rs.500000.00",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "financial_year",
                              "name": "Financial Year"
                           },
                           "value": "2023-2024",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "certificate_instructions",
                              "name": "Certificate Instructions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        }
                     ]
                  },
                  {
                     "display": true,
                     "descriptor": {
                        "code": "additional_info",
                        "name": "Additional Info"
                     },
                     "list": [
                        {
                           "descriptor": {
                              "code": "faq",
                              "name": "Frequently Asked Questions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "terms_conditions",
                              "name": "Terms and Conditions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        }
                     ]
                  }
               ],
               "fulfillment_ids": [
                  "VSP_FUL_1113"
               ]
            }
         ],
         "billing": {
            "name": "Manjunath",
            "organization": {
               "descriptor": {
                  "name": "Namma Yatri",
                  "code": "nammayatri.in"
               },
               "contact": {
                  "phone": "+91-8888888888",
                  "email": "scholarships@nammayatri.in"
               }
            },
            "address": "No 27, XYZ Lane, etc",
            "phone": "+91-9999999999"
         },
         "fulfillments": [
            {
               "state" : {
                  "descriptor" : {
                     "code": "SCHOLARSHIP-APPROVED",
                     "name" : "Application Submitted"
                  },
                  "updated_at" : "2023-02-06T09:55:41.161Z"
               },
               "id": "VSP_FUL_1113",
               "type": "SCHOLARSHIP",
               "tracking": false,
               "agent" : {
                  "person" : {
                     "name" : "Ekstep Foundation SPoc"
                  },
                  "contact" : {
                     "email" : "ekstepsupport@ekstep.com"
                  }
               },
               "customer": {
                  "id": "aadhaar:798677675565",
                  "person": {
                     "name": "Jane Doe",
                     "age": "13",
                     "gender": "female"
                  },
                  "contact": {
                     "phone": "+91-9663088848",
                     "email": "jane.doe@example.com"
                  }
               },
               "stops": [
                  {
                     "type": "APPLICATION-START",
                     "time": {
                        "timestamp": "2023-07-14T18:30:00.000Z"
                     }
                  },
                  {
                     "type": "APPLICATION-END",
                     "time": {
                        "timestamp": "2025-07-13T18:30:00.000Z"
                     }
                  }
               ]
            }
         ],
         "cancellation_terms" : [
            {
               "cancellation_fee" : {
                  "amount" : {
                     "currency" : "INR",
                     "value" : "Penalty upto 5,00,000 INR"
                  }
               }
            }

         ],
         "docs": [
            {
               "descriptor":{
                  "name" :"Application Details",
                  "short_desc" : "To open this document, enter the password sent to your email mayan****@***.com"
               },
               "url" : "https://link-to-the-document.com",
               "mime_type" : "application/pdf"
            }
         ],
         "payments" : [
            {
               "params" :{
                  "bank_code": "IFSC_Code_Of_the_bank",
                  "bank_account_number" :"121212121212",
                  "bank_account_name" : "Account Holder Name"
               }

            }
         ],
         "quote" :{
            "price" : {
               "currency" : "INR",
               "value" : "250000"
            },
            "breakup":[
               {
                  "title": "Tution fee",
                  "price" : {
                     "currency" : "INR",
                     "value" : "150000"
                  }
               },
               {
                  "title": "Hostel fee",
                  "price" : {
                     "currency" : "INR",
                     "value" : "50000"
                  }
               },
               {
                  "title": "Books",
                  "price" : {
                     "currency" : "INR",
                     "value" : "50000"
                  }
               }
            ]
         }
      }
   }
}
```

#### On Status (Scholarship Rejected)

```json
{
   "context": {
      "domain": "onest:financial-support",
      "location": {
         "city": {
            "name": "Bangalore",
            "code": "std:080"
         },
         "country": {
            "name": "India",
            "code": "IND"
         }
      },
      "action": "on_status",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
   "message": {
      "order": {
         "id": "12424kh",
         "provider": {
            "id": "471",
            "descriptor": {
               "name": "XYZ Education Foundation",
               "short_desc" : "Short Description about the Foundation",
               "images": [
                  {
                     "url" : "url of the image of the provider"
                  }
               ]
            },
            "rateable": false
         },
         "items": [
            {
               "id": "SCM_63587501",
               "descriptor": {
                  "name": "XYZ Education Scholarship for Undergraduate Students",
                  "long_desc": "XYZ Education Scholarship for Undergraduate Students"
               },
               "price": {
                  "currency": "INR",
                  "value": "Upto RS.1000 per year"
               },
               "rateable": false,
               "tags": [
                  {
                     "display": true,
                     "descriptor": {
                        "code": "eligibility-criteria",
                        "name": "Eligibility Criteria"
                     },
                     "list": [
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "SC",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "ST",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "OB",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "course_category_criteria",
                              "name": "Course Category Criteria"
                           },
                           "value": "NT",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "gender_criteria",
                              "name": "Gender Criteria"
                           },
                           "value": "ALL",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Thane",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Nagpur",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Yavatmal",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Ahmed Nagar",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Solapur",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "city_criteria",
                              "name": "City Criteria"
                           },
                           "value": "Pune",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "state_criteria",
                              "name": "State Criteria"
                           },
                           "value": "MAHARASHTRA",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "qualification_criteria",
                              "name": "Qualification Criteria"
                           },
                           "value": "Class 10|Min. score=50|Max. score=null",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "qualification_criteria",
                              "name": "Qualification Criteria"
                           },
                           "value": "Class 12|Min. score=60|Max. score=null",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "financial_income_criteria",
                              "name": "Financial Income Criteria"
                           },
                           "value": "Max Family Income - Rs.500000.00",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "financial_year",
                              "name": "Financial Year"
                           },
                           "value": "2023-2024",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "certificate_instructions",
                              "name": "Certificate Instructions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        }
                     ]
                  },
                  {
                     "display": true,
                     "descriptor": {
                        "code": "additional_info",
                        "name": "Additional Info"
                     },
                     "list": [
                        {
                           "descriptor": {
                              "code": "faq",
                              "name": "Frequently Asked Questions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        },
                        {
                           "descriptor": {
                              "code": "terms_conditions",
                              "name": "Terms and Conditions"
                           },
                           "value": "ZMT Education 15JUL23",
                           "display": true
                        }
                     ]
                  }
               ],
               "fulfillment_ids": [
                  "VSP_FUL_1113"
               ]
            }
         ],
         "billing": {
            "name": "Manjunath",
            "organization": {
               "descriptor": {
                  "name": "Namma Yatri",
                  "code": "nammayatri.in"
               },
               "contact": {
                  "phone": "+91-8888888888",
                  "email": "scholarships@nammayatri.in"
               }
            },
            "address": "No 27, XYZ Lane, etc",
            "phone": "+91-9999999999"
         },
         "fulfillments": [
            {
               "state" : {
                  "descriptor" : {
                     "code": "SCHOLARSHIP-APPROVED",
                     "name" : "Application Submitted"
                  },
                  "updated_at" : "2023-02-06T09:55:41.161Z"
               },
               "id": "VSP_FUL_1113",
               "type": "SCHOLARSHIP",
               "tracking": false,
               "agent" : {
                  "person" : {
                     "name" : "Ekstep Foundation SPoc"
                  },
                  "contact" : {
                     "email" : "ekstepsupport@ekstep.com"
                  }
               },
               "customer": {
                  "id": "aadhaar:798677675565",
                  "person": {
                     "name": "Jane Doe",
                     "age": "13",
                     "gender": "female"
                  },
                  "contact": {
                     "phone": "+91-9663088848",
                     "email": "jane.doe@example.com"
                  }
               },
               "stops": [
                  {
                     "type": "APPLICATION-START",
                     "time": {
                        "timestamp": "2023-07-14T18:30:00.000Z"
                     }
                  },
                  {
                     "type": "APPLICATION-END",
                     "time": {
                        "timestamp": "2025-07-13T18:30:00.000Z"
                     }
                  }
               ]
            }
         ],
         "cancellation_terms" : [
            {
               "cancellation_fee" : {
                  "amount" : {
                     "currency" : "INR",
                     "value" : "Penalty upto 5,00,000 INR"
                  }
               }
            }

         ],
         "docs": [
            {
               "descriptor":{
                  "name" :"Application Details",
                  "short_desc" : "To open this document, enter the password sent to your email mayan****@***.com"
               },
               "url" : "https://link-to-the-document.com",
               "mime_type" : "application/pdf"
            }
         ],
         "payments" : [
            {
               "params" :{
                  "bank_code": "IFSC_Code_Of_the_bank",
                  "bank_account_number" :"121212121212",
                  "bank_account_name" : "Account Holder Name"
               }

            }
         ],
         "quote" :{
            "price" : {
               "currency" : "INR",
               "value" : "250000"
            },
            "breakup":[
               {
                  "title": "Tution fee",
                  "price" : {
                     "currency" : "INR",
                     "value" : "150000"
                  }
               },
               {
                  "title": "Hostel fee",
                  "price" : {
                     "currency" : "INR",
                     "value" : "50000"
                  }
               },
               {
                  "title": "Books",
                  "price" : {
                     "currency" : "INR",
                     "value" : "50000"
                  }
               }
            ]
         }
      }
   }
}
```
