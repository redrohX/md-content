---
title: Sales
form:
    name: contact-form
    fields:
        -
            type: spacer
            title: Choose the name of your online therapy room
            text: Your online therapy room needs a name. This name will be the link which all  users click to log on to the online therapy room. Please fill in your preferred web address, preferably the name of your own practice. For example: therapist-johnson.minddistrict.com.
        -
            name: desired_subdomain
            label: Preferred web address
            autofocus: 'on'
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            type: spacer
            title: Choose your package
        -
            type: radio
            name: package
            label:
            options:
              basic_no_video: Basic without video £10
              basic_video: Basic with video £20
              plus_no_video: Plus without video £30
              plus_video: Plus with video £40
        -
            type: spacer
            title: Fill in your details
        -
            type: spacer
            title: Personal information
        -
            type: radio
            name: salutation
            label:
            options:
              mr: Mr.
              mrs: Mrs.
              miss: Miss.
        -
            type: text
            title: first_name
            label: First name
        -
            type: text
            title: last_name
            label: Last name
        -
            type: email
            title: email
            label: Email
        -
            type: spacer
            title: Organisation Details
        -
            type: text
            title: coc_number
            label: Chamber of Commerce number
        -
            type: text
            title: organisation_name
            label: Organisation name
        -
            type: text
            title: address_street
            label: Street name
        -
            type: text
            title: address_number
            label: Number
        -
            type: text
            title: address_addition
            label: Addition
        -
            type: text
            title: address_postcode
            label: Post code
        -
            type: text
            title: address_city
            label: City
        -
            type: text
            title: phone_number
            label: Telephone number

    buttons:
        -
            type: submit
            value: Submit
        -
            type: reset
            value: Reset
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to: ['{{ config.plugins.email.from }}', '{{ form.value.email }}']
                subject: '[Feedback] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: feedback-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            message: 'Thank you for your feedback!'
        -
            display: thankyou
---

A page about sales!

===