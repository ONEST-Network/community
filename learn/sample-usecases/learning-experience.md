# Learning Experience Sample Usecase

### Usecase:&#x20;

Infosys springboard (Provider Platform) creates a diverse range of educational content that is helping simplify education for seekers from all backgrounds. They upload this content on their own platform. Namma Yatri (Seeker Platform) looking for educational content need to find out about Infosys springboard, visit their platform and search for the content based on the name, grade, subject and so on. Outcome is an end-to-end transaction from discovery to post fulfilment.

### UI Flow and API Mapping:

Following is the breakdown of UI steps and APIs used in each step:

1. The driver sees the “Benefits” menu in the bottom tray of the app.
   * search API - Request is made with filters like driver language, course name keywords etc.
   * on\_search API - Response with list of course providers and courses will be received.
2. He selects “Benefits” and can see various options on the page. This page has a section for Insurance and other benefits at the top, followed by the “Learn More - Earn More” section with different courses under it for her/him to select. (Purple Ride, Customer Centric, Safety, etc.)
3. The driver selects a particular course.&#x20;
   * select API - Request is made with selected course ID.
4. Based on the selected course, he gets a list of resources (videos, quizzes, etc.) in the ToC of the course from Springboard through the network.&#x20;
   * on\_select API - Response with complete course details (images, video URLs etc) will be received.
5. He selects the resource (video or quiz) that he would like to play. The relevant resource is highlighted for him/her to play.
   * confirm API - Request is made with user and course details to confirm the course subscription.
6. The selected video will open in the embedded video player on the Namma Yatri app.
   * on\_confirm API - Response with course subscription confirmation details.
7. The next resource (video or quiz) will continue to autoplay.
8. On successful completion of a curated playlist for the particular category, he gets a badge on his profile on the Namma Yatri app that shows his achievement.
   * update API - Request to update the course completed status.
   * on\_update API - Response with completion status, user gets completion certificate.

### Sample JSON Schemas:

#### search API:

```json
{
  "context": {
    "domain": "onest:learning-experience",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "search",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://nammayatri.io",
    "bap_id": "nammayatri.io",
    "bpp_uri": "https://infosys.springboard.io",
    "bpp_id": "infosys.springboard.io",
    "ttl": "PT10M"
  },
  "message": {
    "intent": {
      "item": {
        "descriptor": {
          "name": "english"
        }
      }
    }
  }
}
```

#### on\_search API:

```json
{
  "context": {
    "domain": "onest:learning-experience",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "on_search",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://nammayatri.io",
    "bap_id": "nammayatri.io",
    "bpp_uri": "https://infosys.springboard.io",
    "bpp_id": "infosys.springboard.io",
    "ttl": "PT10M"
  },
  "message": {
    "catalog": {
      "descriptor": {
        "name": "Catalog for English courses"
      },
      "providers": [
        {
          "id": "INFOSYS",
          "descriptor": {
            "name": "Infosys Springboard",
            "short_desc": "Infosys Springboard Digital literacy program",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
                "size_type": "sm"
              }
            ]
          },
          "categories": [
            {
              "id": "LANGUAGE-COURSES",
              "descriptor": {
                "code": "LANGUAGE-COURSES",
                "name": "Language Courses"
              }
            },
            {
              "id": "SKILL-DEVELOPMENT-COURSES",
              "descriptor": {
                "code": "SKILL-DEVELOPMENT-COURSES",
                "name": "Skill development Courses"
              }
            }
          ],
          "items": [
            {
              "id": "d4975df5-b18c-4772-80ad-368669856d52",
              "quantity": {
                "maximum": 1
              },
              "descriptor": {
                "name": "Everyday Conversational English",
                "long_desc": "Everyday Conversational English",
                "images": [
                  {
                    "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
                  }
                ]
              },
              "price": {
                "currency": "INR",
                "value": "0"
              },
              "category_ids": [
                "LANGUAGE-COURSES"
              ],
              "rating": "4.5",
              "tags": [
                {
                  "descriptor": {
                    "code": "course-info",
                    "name": "courseInfo"
                  },
                  "list": [
                    {
                      "descriptor": {
                        "code": "course-instructor",
                        "name": "Course Instructor"
                      },
                      "value": "Prof. Shipra Vaidya"
                    },
                    {
                      "descriptor": {
                        "code": "course-provider",
                        "name": "Course Provider"
                      },
                      "value": "Infosys Springboard"
                    },
                    {
                      "descriptor": {
                        "code": "course-preview",
                        "name": "Course Preview"
                      },
                      "value": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/preview/"
                    }
                  ],
                  "display": true
                }
              ],
              "rateable": true
            },
            {
              "id": "58449592-c4f2-4971-8e23-1da2515042c2",
              "quantity": {
                "maximum": 1
              },
              "descriptor": {
                "name": "English Grammar and Usage",
                "long_desc": "English Grammar and Usage",
                "images": [
                  {
                    "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/english-grammar-and-usage.png"
                  }
                ]
              },
              "price": {
                "currency": "INR",
                "value": "0"
              },
              "category_ids": [
                "LANGUAGE-COURSES"
              ],
              "rating": "4.2",
              "tags": [
                {
                  "descriptor": {
                    "code": "course-info",
                    "name": "courseInfo"
                  },
                  "list": [
                    {
                      "descriptor": {
                        "code": "course-instructor",
                        "name": "Course Instructor"
                      },
                      "value": "Prof. Shipra Vaidya"
                    },
                    {
                      "descriptor": {
                        "code": "course-provider",
                        "name": "Course Provider"
                      },
                      "value": "Infosys Springboard"
                    },
                    {
                      "descriptor": {
                        "code": "course-preview",
                        "name": "Course Preview"
                      },
                      "value": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/english-grammar-and-usage/preview/"
                    }
                  ],
                  "display": true
                }
              ],
              "rateable": true
            }
          ]
        }
      ]
    }
  }
}
```

#### select API:

```json
{
  "context": {
    "domain": "onest:learning-experience",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "select",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://nammayatri.io",
    "bap_id": "nammayatri.io",
    "bpp_uri": "https://infosys.springboard.io",
    "bpp_id": "infosys.springboard.io",
    "ttl": "PT10M"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS"
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52"
        }
      ]
    }
  }
}
```

#### on\_select API:

```json
{
  "context": {
    "domain": "onest:learning-experience",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "on_select",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://nammayatri.io",
    "bap_id": "nammayatri.io",
    "bpp_uri": "https://infosys.springboard.io",
    "bpp_id": "infosys.springboard.io",
    "ttl": "PT10M"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS",
        "descriptor": {
          "name": "Infosys Springboard",
          "short_desc": "Infosys Springboard Digital literacy program",
          "images": [
            {
              "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
              "size_type": "sm"
            }
          ]
        },
        "categories": [
          {
            "id": "LANGUAGE-COURSES",
            "descriptor": {
              "code": "LANGUAGE-COURSES",
              "name": "Language Courses"
            }
          },
          {
            "id": "SKILL-DEVELOPMENT-COURSES",
            "descriptor": {
              "code": "SKILL-DEVELOPMENT-COURSES",
              "name": "Skill development Courses"
            }
          },
          {
            "id": "TECHNICAL-COURSES",
            "descriptor": {
              "code": "TECHNICAL-COURSES",
              "name": "Technical Courses"
            }
          }
        ]
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52",
          "quantity": {
            "maximum": 1
          },
          "descriptor": {
            "name": "Everyday Conversational English",
            "long_desc": "Everyday Conversational English",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
              }
            ]
          },
          "price": {
            "currency": "INR",
            "value": "0"
          },
          "category_ids": [
            "LANGUAGE-COURSES"
          ],
          "rating": "4.5",
          "tags": [
            {
              "descriptor": {
                "code": "course-info",
                "name": "courseInfo"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "course-instructor",
                    "name": "Course Instructor"
                  },
                  "value": "Prof. Shipra Vaidya"
                },
                {
                  "descriptor": {
                    "code": "course-provider",
                    "name": "Course Provider"
                  },
                  "value": "Infosys Springboard"
                },
                {
                  "descriptor": {
                    "code": "course-preview",
                    "name": "Course Preview"
                  },
                  "value": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/preview/"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "code": "course-highlights",
                "name": "Course Highlights"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "highlight",
                    "name": "highlight-1"
                  },
                  "value": "Focusing on clear pronunciation and reducing any strong accents that may impede communication."
                },
                {
                  "descriptor": {
                    "code": "highlight",
                    "name": "highlight-2"
                  },
                  "value": "Expanding everyday vocabulary to facilitate common conversations."
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "code": "course-prerequisites",
                "name": "Course Prerequisites"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "prerequisite-1"
                  },
                  "value": "Should have a basic understanding of English"
                },
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "prerequisite-2"
                  },
                  "value": "Access to a computer or internet to access the course online"
                }
              ],
              "display": true
            }
          ],
          "rateable": true
        }
      ],
      "quote": {
        "price": {
          "currency": "INR",
          "value": "0"
        }
      },
      "fulfillments": [
        {
          "agent": {
            "person": {
              "id": "eng-01-prof",
              "name": "Prof. Shipra Vaidya"
            }
          }
        }
      ],
      "type": "DEFAULT"
    }
  }
}

```

#### confirm API:

```json
{
  "context": {
    "domain": "onest:learning-experience",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "confirm",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://nammayatri.io",
    "bap_id": "nammayatri.io",
    "bpp_uri": "https://infosys.springboard.io",
    "bpp_id": "infosys.springboard.io",
    "ttl": "PT10M"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS"
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52"
        }
      ],
      "billing": {
        "name": "Namma Yatri",
        "organization": {
          "address": "Girija Building, Number 817, Ganapathi Temple Rd",
          "city": "Bengaluru",
          "state": "Karnataka",
          "contact": {
            "email": "example@gmail.in",
            "phone": "+91 1234567890"
          }
        }
      },
      "fulfillments": [
        {
          "customer": {
            "person": {
              "name": "Jhon Doe"
            },
            "contact": {
              "phone": "+91 1234567890",
              "email": "johndoe@gmail.com"
            }
          }
        }
      ],
      "payments": [
        {
          "params": {
            "amount": "0",
            "currency": "INR"
          },
          "status": "PAID"
        }
      ]
    }
  }
}
```

#### on\_confirm API:

```json
{
  "context": {
    "domain": "onest:learning-experience",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "on_confirm",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://nammayatri.io",
    "bap_id": "nammayatri.io",
    "bpp_uri": "https://infosys.springboard.io",
    "bpp_id": "infosys.springboard.io",
    "ttl": "PT10M"
  },
  "message": {
    "order": {
      "id": "d4975df5",
      "provider": {
        "id": "INFOSYS",
        "descriptor": {
          "name": "Infosys Springboard",
          "short_desc": "Infosys Springboard Digital literacy program",
          "images": [
            {
              "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
              "size_type": "sm"
            }
          ]
        }
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52",
          "quantity": {
            "maximum": 1
          },
          "descriptor": {
            "name": "Everyday Conversational English",
            "long_desc": "Everyday Conversational English",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
              }
            ]
          },
          "price": {
            "currency": "INR",
            "value": "0"
          },
          "category_ids": [
            "LANGUAGE-COURSES"
          ],
          "rating": "4.5",
          "tags": [
            {
              "descriptor": {
                "code": "course-info",
                "name": "courseInfo"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "course-instructor",
                    "name": "Course Instructor"
                  },
                  "value": "Prof. Shipra Vaidya"
                },
                {
                  "descriptor": {
                    "code": "course-provider",
                    "name": "Course Provider"
                  },
                  "value": "Infosys Springboard"
                },
                {
                  "descriptor": {
                    "code": "course-link",
                    "name": "Course Link"
                  },
                  "value": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "code": "course-highlights",
                "name": "Course Highlights"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "highlight",
                    "name": "highlight-1"
                  },
                  "value": "Focusing on clear pronunciation and reducing any strong accents that may impede communication."
                },
                {
                  "descriptor": {
                    "code": "highlight",
                    "name": "highlight-2"
                  },
                  "value": "Expanding everyday vocabulary to facilitate common conversations."
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "code": "course-prerequisites",
                "name": "Course Prerequisites"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "prerequisite-1"
                  },
                  "value": "Should have a basic understanding of English"
                },
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "prerequisite-2"
                  },
                  "value": "Access to a computer or internet to access the course online"
                }
              ],
              "display": true
            }
          ],
          "rateable": true
        },
        {
          "id": "c9461edd-628d-46f3-820e-bab42b57d143",
          "parent_item_id": "d4975df5-b18c-4772-80ad-368669856d52",
          "descriptor": {
            "name": "Everyday Conversational English - Chapter 1",
            "long_desc": "Everyday Conversational English - Chapter 1",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english-ch1.png"
              }
            ],
            "media": {
              "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english-ch1/"
            }
          }
        },
        {
          "id": "77223dc6-f6e4-48dd-bf0e-1e43841e651c",
          "parent_item_id": "d4975df5-b18c-4772-80ad-368669856d52",
          "descriptor": {
            "name": "Everyday Conversational English - Chapter 2",
            "long_desc": "Everyday Conversational English - Chapter 2",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english-ch2.png"
              }
            ],
            "media": {
              "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english-ch2/"
            }
          }
        },
        {
          "id": "eae312ed-5a2a-4b95-bed8-407a832b11b8",
          "parent_item_id": "d4975df5-b18c-4772-80ad-368669856d52",
          "descriptor": {
            "name": "Everyday Conversational English - Chapter 3",
            "long_desc": "Everyday Conversational English - Chapter 3",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english-ch3.png"
              }
            ],
            "media": {
              "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english-ch3/"
            }
          }
        }
      ],
      "billing": {
        "name": "Namma Yatri",
        "organization": {
          "address": "Girija Building, Number 817, Ganapathi Temple Rd",
          "city": "Bengaluru",
          "state": "Karnataka",
          "contact": {
            "email": "example@email.in",
            "phone": "+91 1234567890"
          }
        }
      },
      "quote": {
        "price": {
          "currency": "INR",
          "value": "0"
        }
      },
      "fulfillments": [
        {
          "customer": {
            "person": {
              "name": "Jhon Doe"
            },
            "contact": {
              "phone": "+91 1234567890",
              "email": "johndoe@gmail.com"
            }
          },
          "agent": {
            "person": {
              "id": "eng-01-prof",
              "name": "Prof. Shipra Vaidya"
            }
          },
          "state": {
            "descriptor": {
              "code": "order-confirmed",
              "name": "Order Confirmed"
            }
          }
        }
      ],
      "payments": [
        {
          "params": {
            "amount": "0",
            "currency": "INR"
          },
          "status": "PAID"
        }
      ],
      "type": "DEFAULT"
    }
  }
}

```

#### **update API:**

```json
{
  "context": {
    "domain": "onest:learning-experience",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "update",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://nammayatri.io",
    "bap_id": "nammayatri.io",
    "bpp_uri": "https://infosys.springboard.io",
    "bpp_id": "infosys.springboard.io",
    "ttl": "PT10M"
  },
  "message": {
    "order": {
      "fulfillments": [{
            “state”: { 
               “descriptor”: { 
                   “code” : “completed”
               }
           }
      }],
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52"
        }
      ]
    }
  }
}
```

#### **on\_update API:**

```json
{
  "context": {
    "domain": "onest:learning-experience",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "on_update",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://nammayatri.io",
    "bap_id": "nammayatri.io",
    "bpp_uri": "https://infosys.springboard.io",
    "bpp_id": "infosys.springboard.io",
    "ttl": "PT10M"
  },
  "message": {
    "order": {
      "id": "d4975df5",
      "provider": {
        "id": "INFOSYS",
        "descriptor": {
          "name": "Infosys Springboard",
          "short_desc": "Infosys Springboard Digital literacy program",
          "images": [
            {
              "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
              "size_type": "sm"
            }
          ]
        }
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52",
          "quantity": {
            "maximum": 1
          },
          "descriptor": {
            "name": "Everyday Conversational English",
            "long_desc": "Everyday Conversational English",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
              }
            ]
          },
          "price": {
            "currency": "INR",
            "value": "0"
          },
          "category_ids": [
            "LANGUAGE-COURSES"
          ],
          "rating": "4.5",
          "tags": [
            {
              "descriptor": {
                "code": "course-info",
                "name": "courseInfo"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "course-instructor",
                    "name": "Course Instructor"
                  },
                  "value": "Prof. Shipra Vaidya"
                },
                {
                  "descriptor": {
                    "code": "course-provider",
                    "name": "Course Provider"
                  },
                  "value": "Infosys Springboard"
                },
                {
                  "descriptor": {
                    "code": "course-link",
                    "name": "Course Link"
                  },
                  "value": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/"
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "code": "course-highlights",
                "name": "Course Highlights"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "highlight",
                    "name": "highlight-1"
                  },
                  "value": "Focusing on clear pronunciation and reducing any strong accents that may impede communication."
                },
                {
                  "descriptor": {
                    "code": "highlight",
                    "name": "highlight-2"
                  },
                  "value": "Expanding everyday vocabulary to facilitate common conversations."
                }
              ],
              "display": true
            },
            {
              "descriptor": {
                "code": "course-prerequisites",
                "name": "Course Prerequisites"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "prerequisite-1"
                  },
                  "value": "Should have a basic understanding of English"
                },
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "prerequisite-2"
                  },
                  "value": "Access to a computer or internet to access the course online"
                }
              ],
              "display": true
            }
          ],
          "rateable": true
        },
        {
          "id": "c9461edd-628d-46f3-820e-bab42b57d143",
          "parent_item_id": "d4975df5-b18c-4772-80ad-368669856d52",
          "descriptor": {
            "name": "Everyday Conversational English - Chapter 1",
            "long_desc": "Everyday Conversational English - Chapter 1",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english-ch1.png"
              }
            ],
            "media": {
              "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english-ch1/"
            }
          }
        },
        {
          "id": "77223dc6-f6e4-48dd-bf0e-1e43841e651c",
          "parent_item_id": "d4975df5-b18c-4772-80ad-368669856d52",
          "descriptor": {
            "name": "Everyday Conversational English - Chapter 2",
            "long_desc": "Everyday Conversational English - Chapter 2",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english-ch2.png"
              }
            ],
            "media": {
              "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english-ch2/"
            }
          }
        },
        {
          "id": "eae312ed-5a2a-4b95-bed8-407a832b11b8",
          "parent_item_id": "d4975df5-b18c-4772-80ad-368669856d52",
          "descriptor": {
            "name": "Everyday Conversational English - Chapter 3",
            "long_desc": "Everyday Conversational English - Chapter 3",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english-ch3.png"
              }
            ],
            "media": {
              "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english-ch3/"
            }
          }
        }
      ],
      "billing": {
        "name": "Namma Yatri",
        "organization": {
          "address": "Girija Building, Number 817, Ganapathi Temple Rd",
          "city": "Bengaluru",
          "state": "Karnataka",
          "contact": {
            "email": "nammayatri.support@juspay.in",
            "phone": "+91 80 68501060"
          }
        }
      },
      "quote": {
        "price": {
          "currency": "INR",
          "value": "0"
        }
      },
      "fulfillments": [
        {
          "customer": {
            "person": {
              "name": "Jhon Doe",
              "creds": {
                "type": "VerifiableCredential",
                "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/certificate"
              }
            },
            "contact": {
              "phone": "+91 1234567890",
              "email": "jhondoe@gmail.com"
            }
          },
          "agent": {
            "person": {
              "id": "eng-01-prof",
              "name": "Prof. Shipra Vaidya"
            }
          },
          "state": {
            "descriptor": {
              "code": "completed",
              "name": "Status of the course progress"
            }
          }
        }
      ],
      "payments": [
        {
          "params": {
            "amount": "0",
            "currency": "INR"
          },
          "status": "PAID"
        }
      ],
      "type": "DEFAULT"
    }
  }
}

```
