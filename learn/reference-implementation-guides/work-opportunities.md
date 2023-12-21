# Work Opportunities

### Usecase:

Job Hub is acting as provider platform(BPP) which hosts the jobs and Worker Hub is acting as seeker platform(BAP) which helps the workers to find jobs.

### Flow Diagram:

<figure><img src="../../.gitbook/assets/work-opportunities.jpg" alt=""><figcaption></figcaption></figure>

### API Mapping and Sample JSON's:

1. BAP will make search request with an intent, ex: job name, job provider, location, skills etc.

#### Search API (Search By Job Name)

```json
{
  "context": {
    "domain": "onest:work-opportunities",
    "action": "search",
    "version": "1.1.0",
    "bap_id": "worker-hub.bap.io",
    "bap_uri": "https://worker-hub.bap.io/",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
    "message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
    "timestamp": "2022-10-11T09:55:41.161Z",
    "ttl": "PT30S"
  },
  "message": {
    "intent": {
      "item": {
        "descriptor": {
          "name": "Engineer"
        }
      }
    }
  }
}

```

2. BPP will create a catalogue containing jobs with matching criteria and sends it as on\_search request.

#### On Search API&#x20;

The request will contain only minimal details about the job like job name, job description, location etc.

```
{
  "context": {
    "domain": "onest:work-opportunities",
    "action": "on_search",
    "version": "1.1.0",
    "bap_id": "worker-hub.bap.io",
    "bap_uri": "https://worker-hub.bap.io",
    "bpp_id": "job-hub.bpp.io",
    "bpp_uri": "https://job-hub.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
    "message_id": "672f774c-4281-44dd-b1c2-84222a3d771e",
    "timestamp": "2023-02-22T11:45:10.1712958+00:00",
    "ttl": "P1M"
  },
  "message": {
    "catalog": {
      "descriptor": {
        "name": "Affindi Jobs"
      },
      "payments": [],
      "providers": [
        {
          "id": "1",
          "descriptor": {
            "name": "Affinidi",
            "short_desc": "Short Description about the company",
            "images": [
              {
                "url": "url of the image of the provider"
              }
            ]
          },
         "fulfillments": [
          {
            "id": "1",
            "type": "remote"
          },
          {
            "id": "2",
            "type": "hybrid"
          },
          {
            "id": "3",
            "type": "Onsite"
          }
          ],
          "locations": [
            {
              "id": "L1",
              "city": {
                "name": "Pune",
                "code": "std:020"
              },
              "state": {
                "name": "Maharastra",
                "code": "MH"
              }
            },
            {
              "id": "L2",
              "city": {
                "name": "Thane",
                "code": "std:022"
              },
              "state": {
                "name": "Maharastra",
                "code": "MH"
              }
            },
            {
              "id": "L3",
              "city": {
                "name": "Lucknow",
                "code": "std:0522"
              },
              "state": {
                "name": "Uttar Pradesh",
                "code": "UP"
              }
            }
          ],
          "items": [
            {
              "id": "D7F8606A370DA9966DF15E62A81C374B",
              "descriptor": {
                "name": "Database Engineer",
                "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
              },
              "location_ids": [
                "L1"
              ],
              "fulfillment_ids": [
                "1",
                "2",
                "3"
              ]
            },
            {
              "id": "0253719F295521CED39EC9C2F3C8DCDE",
              "descriptor": {
                "name": "Fullstack Engineer",
                "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
              },
              "location_ids": [
                "L2"
              ],
               "fulfillment_ids": [
                  "1",
                  "2",
                  "3"
               ]
            }
          ]
        }
      ]
    }
  }
}

```

3. BAP will receive the on\_search request and displays the list of jobs to the user. Once the user chooses a job, BAP will make select API with item ID to get the complete details about the job.

#### Select API:

```
{
    "context": {
        "domain": "onest:work-opportunities",
        "action": "select",
        "version": "1.1.0",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io",
        "bpp_id": "job-hub.bpp.io",
        "bpp_uri": "https://job-hub.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
        "timestamp": "2023-02-14T12:11:46.1295616+00:00",
        "ttl": "P1M"
    },
    "message": {
        "order": {
            "provider":{
                "id":"1"
            },
            "items": [
                {
                    "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca"
                }
            ]
        }
    }
}

```

4. BPP will receive the select request and check if the listing is still valid. If the listing is still valid, BPP will send the on\_select call with complete details of the job listing.

#### On Select API

```
{
  "context": {
    "domain": "onest:work-opportunities",
    "version": "1.1.0",
    "action": "on_select",
    "bap_id": "worker-hub.bap.io",
    "bap_uri": "https://worker-hub.bap.io",
    "bpp_id": "job-hub.bpp.io",
    "bpp_uri": "https://job-hub.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
    "message_id": "c8e3968c-cd78-4e46-aa34-0d541e46bd73",
    "ttl": "PT10M",
    "timestamp": "2023-02-22T11:50:46.742Z"
  },
  "message": {
    "order": {
      "provider": {
        "descriptor": {
          "name": "Affinidi"
        },
        "fulfillments": [
          {
            "id": "1",
            "type": "remote"
          },
          {
            "id": "2",
            "type": "hybrid"
          },
          {
            "id": "3",
            "type": "Onsite"
          }
        ],
        "locations": [
          {
            "id": "L1",
            "city": {
              "name": "Pune",
              "code": "std:020"
            },
            "state": {
              "name": "Maharastra",
              "code": "MH"
            }
          }
        ]
      },
      "items": [
        {
          "id": "0253719F295521CED39EC9C2F3C8DCDE",
          "descriptor": {
            "name": "Fullstack Engineer",
            "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
          },
          "fulfillment_ids": [
            "1",
            "2",
            "3"
          ],
          "location_ids": [
            "L1"
          ],
          "time": {
            "range": {
              "start": "2023-01-03T13:23:01+00:00",
              "end": "2023-02-03T13:23:01+00:00"
            }
          },
          "tags": [
            {
              "descriptor": {
                "name": "Minimum Educational Qualifications"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "Bachelors"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Preferred Educational Qualifications"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "Masters"
                },
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "PhD"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Work Experience"
              },
              "list": [
                {
                  "value": "3 years of Software Development Experience"
                },
                {
                  "value": "2 years of Technical Leadership Experience"
                },
                {
                  "value": "3 years of experience working in a complex, matrixed organization"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Responsibilities"
              },
              "list": [
                {
                  "value": "Build frontend experiences for our tools (Web, PWA and React Native) "
                },
                {
                  "value": "Articulate a long term technical direction and vision for building, maintaining, and scaling our web and mobile platforms"
                },
                {
                  "value": "Create trustworthy user experiences by building interfaces that are simple, easy to comprehend, performant and reliable using modern tools like React, React Native, Typescript, Node.js, Jest and Webpack."
                },
                {
                  "value": "Mentor and train other team members on design techniques and coding standards. "
                },
                {
                  "value": "Own all aspects of our front-end architecture "
                },
                {
                  "value": "Contribute to process improvements and build a high-performance engineering culture "
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Employment Information",
                "code": "employment-info"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "Employment Duration Type",
                    "code": "emp-duration-type"
                  },
                  "value": "FULL_TIME"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "skill requirement",
                "code": "Skills"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "You have 8+ years of engineering experience, predominantly in shipping user-facing production features"
                  }
                },
                {
                  "descriptor": {
                    "name": "You are an expert in React.js and React Native, ideally using TypeScript language extensions  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have a good understanding of JavaScript Design Patterns "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have good experience writing front end test cases  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You’re familiar with current trends and best practices in front-end architecture, including performance, security and usability.  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You’re familiar with product and design lifecycles, and collaborating closely with designers, engineers, and product managers "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience with Test Driven Development and know when to apply it."
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience working on AWS or other cloud stacks and Docker.  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience building systems with high data protection requirements, anonymous data and data encryption. "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience with IaaC. "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have worked on building responsive UI using React Native. "
                  }
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Salary Compensation",
                "code": "salary-info"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "CTC Range"
                  },
                  "value": "50000-80000"
                },
                {
                  "descriptor": {
                    "name": "baseSalary"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "variableSalary"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "allowance"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "commission"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "overtime"
                  },
                  "value": "8"
                }
              ],
              "display": true
            }
          ]
        }
      ],
      "type": "DEFAULT"
    }
  }
}

```

5. BAP sends the customer details to the BPP in the init API. This is the initializing step of the job application process.

#### Init API

```
{
  "context": {
    "domain": "onest:work-opportunities",
    "action": "init",
    "version": "1.1.0",
    "bap_id": "worker-hub.bap.io",
    "bap_uri": "https://worker-hub.bap.io",
    "bpp_id": "job-hub.bpp.io",
    "bpp_uri": "https://job-hub.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
    "message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
    "timestamp": "2023-02-14T12:11:46.1295616+00:00",
    "ttl": "P1M"
  },
  "message": {
    "order": {
      "provider": {
        "id": "1"
      },
      "items": [
        {
          "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca"
        },
       ,
       "fulfillment_ids": [
            "1"
        ]
      ],
      "fulfillments": [
        {
          "id": "1",
          "customer": {
            "person": {
              "name": "Sanjay",
              "gender": "Male",
              "age": "35",
              "skills": [
                {
                  "code": "Android",
                  "name": "Android"
                },
                {
                  "code": "AWS",
                  "name": "AWS"
                }
              ],
              "languages": [
                {
                  "code": "en",
                  "name": "english"
                },
                {
                  "code": "ml",
                  "name": "Malayalam"
                },
                {
                  "code": "hi",
                  "name": "Hindi"
                }
              ],
              "tags": [
                {
                  "code": "current-experience",
                  "list": [
                    {
                      "descriptor": {
                        "code": "exp-years",
                        "name": "Experience"
                      },
                      "value": "P4Y2M" //ISO Duration Format 
                    },
                    {
                      "descriptor": {
                        "code": "current-company",
                        "name": "Current Company"
                      },
                      "value": "ABC tech"
                    }
                  ]
                },
                {
                  "code": "salary-details",
                  "list": [
                    {
                      "descriptor": {
                        "code": "expected-salary",
                        "name": "Expected Salary"
                      },
                      "value": "80000"
                    },
                    {
                      "descriptor": {
                        "code": "current-salary",
                        "name": "Current Salary"
                      },
                      "value": "50000"
                    }
                  ]
                },
                {
                  "code": "documents",
                  "list": [
                    {
                      "descriptor": {
                        "code": "resume",
                        "name": "resume"
                      },
                      "value": "https://link-to-the-document.com"
                    }
                  ]
                }
              ]
            },
            "contact": {
              "phone": "9999999999999",
              "email": "abc@abc.bc"
            }
          }
        }
      ]
    }
  }
}
```

6. If BPP want to collect additional details of the user, he will send an xinput form in the on\_init request.\
   \
   If BPP has multiple forms to collect the data, he will make on\_init request with the form number(current index) and total number of forms(max index). BPP should generate the xinput form with transaction id(request.context.transaction\_id). So that the forms can be tagged with a lifecyle.\
   \
   BAP should render the xinput form on the UI and collect all the details.\
   \
   If there are no required xinput forms, the BAP can confirm the order via /confirm API.\
   \
   [Link](https://github.com/beckn/DSEP-Specification/blob/draft/examples/financial-support/forms/scholarship-application-form.html) : Example xinput form

#### On Init API

```
{
  "context": {
    "domain": "onest:work-opportunities",
    "action": "on_init",
    "version": "1.1.0",
    "bap_id": "worker-hub.bap.io",
    "bap_uri": "https://worker-hub.bap.io",
    "bpp_id": "job-hub.bpp.io",
    "bpp_uri": "https://job-hub.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
    "message_id": "af58aa7b-6745-47d0-9b0d-62dcb262ee87",
    "timestamp": "2023-02-23T10:14:05.5579055+00:00",
    "ttl": "P1M"
  },
  "message": {
    "order": {
      "provider": {
        "descriptor": {
          "name": "Affinidi"
        },
        "locations": [
          {
            "id": "L1",
            "city": {
              "name": "Pune",
              "code": "std:020"
            },
            "state": {
              "name": "Maharastra",
              "code": "MH"
            }
          }
        ]
      },
      "items": [
        {
          "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
          "descriptor": {
            "name": "Fullstack Engineer",
            "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
          },
          "fulfillment_ids": [
            "1"
          ],
          "location_ids": [
            "L1"
          ],
          "time": {
            "range": {
              "start": "2023-01-03T13:23:01+00:00",
              "end": "2023-02-03T13:23:01+00:00"
            }
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
                    "max": 1
                },
                "headings": [
                    "Candidate Details"
                ]
            },
            "form": {
                "mime_type": "text/html",
                "url": "https://6vs8xnx5i7.jobhub.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f-1",
                "resubmit": false
            }
          },
          "tags": [
            {
              "descriptor": {
                "name": "Minimum Educational Qualifications"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "Bachelors"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Preferred Educational Qualifications"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "Masters"
                },
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "PhD"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Work Experience"
              },
              "list": [
                {
                  "value": "3 years of Software Development Experience"
                },
                {
                  "value": "2 years of Technical Leadership Experience"
                },
                {
                  "value": "3 years of experience working in a complex, matrixed organization"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Responsibilities"
              },
              "list": [
                {
                  "value": "Build frontend experiences for our tools (Web, PWA and React Native) "
                },
                {
                  "value": "Articulate a long term technical direction and vision for building, maintaining, and scaling our web and mobile platforms"
                },
                {
                  "value": "Create trustworthy user experiences by building interfaces that are simple, easy to comprehend, performant and reliable using modern tools like React, React Native, Typescript, Node.js, Jest and Webpack."
                },
                {
                  "value": "Mentor and train other team members on design techniques and coding standards. "
                },
                {
                  "value": "Own all aspects of our front-end architecture "
                },
                {
                  "value": "Contribute to process improvements and build a high-performance engineering culture "
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Employment Information",
                "code": "employment-info"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "Employment Duration Type",
                    "code": "emp-duration-type"
                  },
                  "value": "FULL_TIME"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "skill requirement",
                "code": "Skills"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "You have 8+ years of engineering experience, predominantly in shipping user-facing production features"
                  }
                },
                {
                  "descriptor": {
                    "name": "You are an expert in React.js and React Native, ideally using TypeScript language extensions  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have a good understanding of JavaScript Design Patterns "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have good experience writing front end test cases  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You’re familiar with current trends and best practices in front-end architecture, including performance, security and usability.  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You’re familiar with product and design lifecycles, and collaborating closely with designers, engineers, and product managers "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience with Test Driven Development and know when to apply it."
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience working on AWS or other cloud stacks and Docker.  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience building systems with high data protection requirements, anonymous data and data encryption. "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience with IaaC. "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have worked on building responsive UI using React Native. "
                  }
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Salary Compensation",
                "code": "salary-info"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "CTC Range"
                  },
                  "value": "50000-80000"
                },
                {
                  "descriptor": {
                    "name": "baseSalary"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "variableSalary"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "allowance"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "commission"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "overtime"
                  },
                  "value": "8"
                }
              ],
              "display": true
            }
          ]
        }
      ],
      "fulfillments": [
        {
          "id": "1",
          "customer": {
            "person": {
              "name": "Sanjay",
              "gender": "Male",
              "age": "35",
              "skills": [
                {
                  "code": "Android",
                  "name": "Android"
                },
                {
                  "code": "AWS",
                  "name": "AWS"
                }
              ],
              "languages": [
                {
                  "code": "en",
                  "name": "english"
                },
                {
                  "code": "ml",
                  "name": "Malayalam"
                },
                {
                  "code": "hi",
                  "name": "Hindi"
                }
              ],
              "tags": [
                {
                  "code": "current-experience",
                  "list": [
                    {
                      "descriptor": {
                        "code": "exp-years",
                        "name": "Experience"
                      },
                      "value": "P4Y2M"
                    },
                    {
                      "descriptor": {
                        "code": "current-company",
                        "name": "Current Company"
                      },
                      "value": "ABC tech"
                    }
                  ]
                },
                {
                  "code": "salary-details",
                  "list": [
                    {
                      "descriptor": {
                        "code": "expected-salary",
                        "name": "Expected Salary"
                      },
                      "value": "80000"
                    },
                    {
                      "descriptor": {
                        "code": "current-salary",
                        "name": "Current Salary"
                      },
                      "value": "50000"
                    }
                  ]
                },
                {
                  "code": "documents",
                  "list": [
                    {
                      "descriptor": {
                        "code": "resume",
                        "name": "resume"
                      },
                      "value": "https://link-to-the-document.com"
                    }
                  ]
                }
              ]
            },
            "contact": {
              "phone": "9999999999999",
              "email": "abc@abc.bc"
            }
          }
        }
      ]
    }
  }
}
```

#### On Init API step 2 (post form submission)

```
{
  "context": {
    "domain": "onest:work-opportunities",
    "action": "on_init",
    "version": "1.1.0",
    "bap_id": "worker-hub.bap.io",
    "bap_uri": "https://worker-hub.bap.io",
    "bpp_id": "job-hub.bpp.io",
    "bpp_uri": "https://job-hub.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
    "message_id": "af58aa7b-6745-47d0-9b0d-62dcb262ee87",
    "timestamp": "2023-02-23T10:14:05.5579055+00:00",
    "ttl": "P1M"
  },
  "message": {
    "order": {
      "provider": {
        "descriptor": {
          "name": "Affinidi"
        },
        "locations": [
          {
            "id": "L1",
            "city": {
              "name": "Pune",
              "code": "std:020"
            },
            "state": {
              "name": "Maharastra",
              "code": "MH"
            }
          }
        ]
      },
      "items": [
        {
          "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
          "descriptor": {
            "name": "Fullstack Engineer",
            "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
          },
          "fulfillment_ids": [
            "1"
          ],
          "location_ids": [
            "L1"
          ],
          "time": {
            "range": {
              "start": "2023-01-03T13:23:01+00:00",
              "end": "2023-02-03T13:23:01+00:00"
            }
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
                    "max": 1
                },
                "headings": [
                    "Candidate Details"
                ]
            },
            "form": {
                "mime_type": "text/html",
                "url": "https://6vs8xnx5i7.jobhub.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f-1",
                "resubmit": false,
                "auth": {
                    "descriptor": {
                        "code": "jwt"
                    },
                    "value": "eyJhbGciOiJIUzI.eyJzdWIiOiIxMjM0NTY3O.SflKxwRJSMeKKF2QT4"
                }
            }
          },
          "tags": [
            {
              "descriptor": {
                "name": "Minimum Educational Qualifications"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "Bachelors"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Preferred Educational Qualifications"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "Masters"
                },
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "PhD"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Work Experience"
              },
              "list": [
                {
                  "value": "3 years of Software Development Experience"
                },
                {
                  "value": "2 years of Technical Leadership Experience"
                },
                {
                  "value": "3 years of experience working in a complex, matrixed organization"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Responsibilities"
              },
              "list": [
                {
                  "value": "Build frontend experiences for our tools (Web, PWA and React Native) "
                },
                {
                  "value": "Articulate a long term technical direction and vision for building, maintaining, and scaling our web and mobile platforms"
                },
                {
                  "value": "Create trustworthy user experiences by building interfaces that are simple, easy to comprehend, performant and reliable using modern tools like React, React Native, Typescript, Node.js, Jest and Webpack."
                },
                {
                  "value": "Mentor and train other team members on design techniques and coding standards. "
                },
                {
                  "value": "Own all aspects of our front-end architecture "
                },
                {
                  "value": "Contribute to process improvements and build a high-performance engineering culture "
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Employment Information",
                "code": "employment-info"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "Employment Duration Type",
                    "code": "emp-duration-type"
                  },
                  "value": "FULL_TIME"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "skill requirement",
                "code": "Skills"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "You have 8+ years of engineering experience, predominantly in shipping user-facing production features"
                  }
                },
                {
                  "descriptor": {
                    "name": "You are an expert in React.js and React Native, ideally using TypeScript language extensions  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have a good understanding of JavaScript Design Patterns "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have good experience writing front end test cases  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You’re familiar with current trends and best practices in front-end architecture, including performance, security and usability.  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You’re familiar with product and design lifecycles, and collaborating closely with designers, engineers, and product managers "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience with Test Driven Development and know when to apply it."
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience working on AWS or other cloud stacks and Docker.  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience building systems with high data protection requirements, anonymous data and data encryption. "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience with IaaC. "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have worked on building responsive UI using React Native. "
                  }
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Salary Compensation",
                "code": "salary-info"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "CTC Range"
                  },
                  "value": "50000-80000"
                },
                {
                  "descriptor": {
                    "name": "baseSalary"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "variableSalary"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "allowance"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "commission"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "overtime"
                  },
                  "value": "8"
                }
              ],
              "display": true
            }
          ]
        }
      ],
      "fulfillments": [
        {
          "id": "1",
          "customer": {
            "person": {
              "name": "Sanjay",
              "gender": "Male",
              "age": "35",
              "skills": [
                {
                  "code": "Android",
                  "name": "Android"
                },
                {
                  "code": "AWS",
                  "name": "AWS"
                }
              ],
              "languages": [
                {
                  "code": "en",
                  "name": "english"
                },
                {
                  "code": "ml",
                  "name": "Malayalam"
                },
                {
                  "code": "hi",
                  "name": "Hindi"
                }
              ],
              "tags": [
                {
                  "code": "current-experience",
                  "list": [
                    {
                      "descriptor": {
                        "code": "exp-years",
                        "name": "Experience"
                      },
                      "value": "P4Y2M"
                    },
                    {
                      "descriptor": {
                        "code": "current-company",
                        "name": "Current Company"
                      },
                      "value": "ABC tech"
                    }
                  ]
                },
                {
                  "code": "salary-details",
                  "list": [
                    {
                      "descriptor": {
                        "code": "expected-salary",
                        "name": "Expected Salary"
                      },
                      "value": "80000"
                    },
                    {
                      "descriptor": {
                        "code": "current-salary",
                        "name": "Current Salary"
                      },
                      "value": "50000"
                    }
                  ]
                },
                {
                  "code": "documents",
                  "list": [
                    {
                      "descriptor": {
                        "code": "resume",
                        "name": "resume"
                      },
                      "value": "https://link-to-the-document.com"
                    }
                  ]
                }
              ]
            },
            "contact": {
              "phone": "9999999999999",
              "email": "abc@abc.bc"
            }
          }
        }
      ]
    }
  }
}
```

7. BAP confirms user wants to submit the job application.

#### confirm API

```
{
    "context": {
        "domain": "onest:work-opportunities",
        "version": "1.1.0",
        "action": "confirm",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io",
        "bpp_id": "job-hub.bpp.io",
        "bpp_uri": "https://job-hub.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "481a01fc-4b45-4d49-9558-c6a7dfad8b75",
        "ttl": "PT10M",
        "timestamp": "2023-02-23T08:09:02.172Z"
    },
    "message": {
        "order": {
            "provider": {
                "id": "1"
            },
            "items": [
                {
                    "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
                    "fulfillment_ids": [
                        "1"
                    ]
                }
            ],
            "fulfillments": [
                {
                    "id": "1",
                    "customer": {
                        "person": {
                            "name": "Sanjay",
                            "gender": "Male",
                            "age": "35",
                            "skills": [
                                {
                                    "code": "Android",
                                    "name": "Android"
                                },
                                {
                                    "code": "AWS",
                                    "name": "AWS"
                                }
                            ],
                            "languages": [
                                {
                                    "code": "en",
                                    "name": "english"
                                },
                                {
                                    "code": "ml",
                                    "name": "Malayalam"
                                },
                                {
                                    "code": "hi",
                                    "name": "Hindi"
                                }
                            ],
                            "tags": [
                                {
                                    "code": "current-experience",
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "exp-years",
                                                "name": "Experience"
                                            },
                                            "value": "P4Y2M"
                                        },
                                        {
                                            "descriptor": {
                                                "code": "current-company",
                                                "name": "Current Company"
                                            },
                                            "value": "ABC tech"
                                        }
                                    ]
                                },
                                {
                                    "code": "salary-details",
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "expected-salary",
                                                "name": "Expected Salary"
                                            },
                                            "value": "80000"
                                        },
                                        {
                                            "descriptor": {
                                                "code": "current-salary",
                                                "name": "Current Salary"
                                            },
                                            "value": "50000"
                                        }
                                    ]
                                },
                                {
                                    "code": "documents",
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "resume",
                                                "name": "resume"
                                            },
                                            "value": "https://link-to-the-document.com"
                                        }
                                    ]
                                }
                            ]
                        },
                        "contact": {
                            "phone": "9999999999999",
                            "email": "abc@abc.bc"
                        }
                    }
                }
            ]
        }
    }
}
```

8. BPP sends confirmation of submission of job application.

#### On Confirm API

```
{
  "context": {
    "domain": "onest:work-opportunities",
    "action": "on_confirm",
    "version": "1.1.0",
    "bap_id": "worker-hub.bap.io",
    "bap_uri": "https://worker-hub.bap.io",
    "bpp_id": "job-hub.bpp.io",
    "bpp_uri": "https://job-hub.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
    "message_id": "8cbb5e99-5d06-4855-81e9-a4fc8013dbff",
    "timestamp": "2023-02-23T08:20:06.0674501+00:00",
    "ttl": "P1M"
  },
  "message": {
    "order": {
      "id": "1677140405881",
      "provider": {
        "descriptor": {
          "name": "Affinidi"
        },
        "locations": [
          {
            "id": "L1",
            "city": {
              "name": "Pune",
              "code": "std:020"
            },
            "state": {
              "name": "Maharastra",
              "code": "MH"
            }
          }
        ]
      },
      "items": [
        {
          "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
          "descriptor": {
            "name": "Fullstack Engineer",
            "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
          },
          "fulfillment_ids": [
            "1"
          ],
          "location_ids": [
            "L1"
          ],
          "time": {
            "range": {
              "start": "2023-01-03T13:23:01+00:00",
              "end": "2023-02-03T13:23:01+00:00"
            }
          },
          "tags": [
            {
              "descriptor": {
                "name": "Minimum Educational Qualifications"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "Bachelors"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Preferred Educational Qualifications"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "Masters"
                },
                {
                  "descriptor": {
                    "name": "degree",
                    "code": "degree"
                  },
                  "value": "PhD"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Work Experience"
              },
              "list": [
                {
                  "value": "3 years of Software Development Experience"
                },
                {
                  "value": "2 years of Technical Leadership Experience"
                },
                {
                  "value": "3 years of experience working in a complex, matrixed organization"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Responsibilities"
              },
              "list": [
                {
                  "value": "Build frontend experiences for our tools (Web, PWA and React Native) "
                },
                {
                  "value": "Articulate a long term technical direction and vision for building, maintaining, and scaling our web and mobile platforms"
                },
                {
                  "value": "Create trustworthy user experiences by building interfaces that are simple, easy to comprehend, performant and reliable using modern tools like React, React Native, Typescript, Node.js, Jest and Webpack."
                },
                {
                  "value": "Mentor and train other team members on design techniques and coding standards. "
                },
                {
                  "value": "Own all aspects of our front-end architecture "
                },
                {
                  "value": "Contribute to process improvements and build a high-performance engineering culture "
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Employment Information",
                "code": "employment-info"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "Employment Duration Type",
                    "code": "emp-duration-type"
                  },
                  "value": "FULL_TIME"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "skill requirement",
                "code": "Skills"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "You have 8+ years of engineering experience, predominantly in shipping user-facing production features"
                  }
                },
                {
                  "descriptor": {
                    "name": "You are an expert in React.js and React Native, ideally using TypeScript language extensions  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have a good understanding of JavaScript Design Patterns "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have good experience writing front end test cases  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You’re familiar with current trends and best practices in front-end architecture, including performance, security and usability.  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You’re familiar with product and design lifecycles, and collaborating closely with designers, engineers, and product managers "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience with Test Driven Development and know when to apply it."
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience working on AWS or other cloud stacks and Docker.  "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience building systems with high data protection requirements, anonymous data and data encryption. "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have experience with IaaC. "
                  }
                },
                {
                  "descriptor": {
                    "name": "You have worked on building responsive UI using React Native. "
                  }
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "name": "Salary Compensation",
                "code": "salary-info"
              },
              "list": [
                {
                  "descriptor": {
                    "name": "CTC Range"
                  },
                  "value": "50000-80000"
                },
                {
                  "descriptor": {
                    "name": "baseSalary"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "variableSalary"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "allowance"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "commission"
                  },
                  "value": "60000"
                },
                {
                  "descriptor": {
                    "name": "overtime"
                  },
                  "value": "8"
                }
              ],
              "display": true
            }
          ]
        }
      ],
      "fulfillments": [
        {
          "id": "1",
          "customer": {
            "person": {
              "name": "Sanjay",
              "gender": "Male",
              "age": "35",
              "skills": [
                {
                  "code": "Android",
                  "name": "Android"
                },
                {
                  "code": "AWS",
                  "name": "AWS"
                }
              ],
              "languages": [
                {
                  "code": "en",
                  "name": "english"
                },
                {
                  "code": "ml",
                  "name": "Malayalam"
                },
                {
                  "code": "hi",
                  "name": "Hindi"
                }
              ],
              "tags": [
                {
                  "code": "current-experience",
                  "list": [
                    {
                      "descriptor": {
                        "code": "exp-years",
                        "name": "Experience"
                      },
                      "value": "P4Y2M"
                    },
                    {
                      "descriptor": {
                        "code": "current-company",
                        "name": "Current Company"
                      },
                      "value": "ABC tech"
                    }
                  ]
                },
                {
                  "code": "salary-details",
                  "list": [
                    {
                      "descriptor": {
                        "code": "expected-salary",
                        "name": "Expected Salary"
                      },
                      "value": "80000"
                    },
                    {
                      "descriptor": {
                        "code": "current-salary",
                        "name": "Current Salary"
                      },
                      "value": "50000"
                    }
                  ]
                },
                {
                  "code": "documents",
                  "list": [
                    {
                      "descriptor": {
                        "code": "resume",
                        "name": "resume"
                      },
                      "value": "https://link-to-the-document.com"
                    }
                  ]
                }
              ]
            },
            "contact": {
              "phone": "9999999999999",
              "email": "abc@abc.bc"
            }
          }
        }
      ]
    }
  }
}

```

### Skill Codes

[https://www.ncs.gov.in/Documents/National%20Classification%20of%20Occupations%20\_Vol%20I-%202015.pdf](https://www.ncs.gov.in/Documents/National%20Classification%20of%20Occupations%20\_Vol%20I-%202015.pdf)
