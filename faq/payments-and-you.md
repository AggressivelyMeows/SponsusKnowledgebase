---
description: 'Payments can be so stressful, let us answer some of your biggest worries!'
---

# Payments and you

## Does Sponsus store credit cards?

**No**. Sponsus does not store credit cards, not even the post address or CVC. We use Stripe to store and protect credit card numbers as they are typed in. What happens is that when you click "add card", we ask Stripe to take whats inside the input box and "tokenize" it. The token that Sponsus gets back represents your card in future payments, allowing us to charge the card for sponsorships or donations without storing your payment information.

**Sponsus cannot, not during, not after, access your credit card numbers.**

## What is PCI compliant mean?

PCI-DSS is the global security standard for all entities that store, process, or transmit cardholder data and/or sensitive authentication data. PCI DSS sets a baseline level of protection for consumers and helps reduce fraud and data breaches across the entire payment ecosystem. It is applicable to any organization that accepts or processes payment cards.

**In summary: Any time a company has to process sensitive data, it must do so in a secure and safe manor.**

Sponsus is compliant under PCI SAQ-A. This means that Sponsus does the following to ensure your datas security:

`Card-not-present merchants (e-commerce or mail/telephone-order), that have fully outsourced all cardholder data functions to PCI DSS compliant third-party service providers, with no electronic storage, processing, or transmission of any cardholder data on the merchant’s systems or premises.`

**At no point does your credit card number hit our servers. They are encrypted and sent to Stripe in browser.**

## Why am I being asked to sign into my bank?

The **3D Secure** standard—often known by its branded names like Visa Secure, Mastercard Identity Check, or American Express SafeKey—aims to reduce fraud and provide added security to online payments. Beginning in late 2019, banks are expected to gradually start supporting a new version of 3D Secure.

Sponsus uses this feature of banks to ensure that the person signing up is doing so with a legitimate card, reducing fraud and chargebacks.

The enforcement of [Strong Customer Authentication](https://stripe.com/guides/strong-customer-authentication) \(SCA\) in September 2019 makes 3D Secure 2 all the more important if you are doing business in Europe. As this new regulation will require you to apply more authentication on European payments, the improved user experience of 3D Secure 2 can help reduce the negative impact on conversion.



