=============
Configuration
=============

These values defined in ``settings.py`` affect the application:

* ``DEFAULT_FROM_EMAIL``: This is the sender of the email sent with your
  contact form.

  .. note::
      (Some mail servers do not allow sending messages from an
      address that is different than the one used for SMTP authentication.)

* ``ENVELOPE_EMAIL_RECIPIENTS``: A list of e-mail addresses of people who will
  receive the message. For backwards compatibility reasons, the default value
  is a list where the only element is ``DEFAULT_FROM_EMAIL``.

  .. versionadded:: 0.3.1

* ``ENVELOPE_CONTACT_CHOICES``: A tuple of pairs describing possible choices
  for message type. The default is defined as follows::
  
    DEFAULT_CONTACT_CHOICES = (
        ('',    u"Choose"),
        (10,    u"A general question regarding the website"),
        (None,   u"Other"),
    )
  
  The numeric values are pretty much arbitrary. Remember to leave an empty
  value for the choice when the field is initially unset ("Choose").

* ``ENVELOPE_SUBJECT_INTRO``: The prefix for subject line of the email message.
  This is different than ``EMAIL_SUBJECT_PREFIX`` which is global for the whole
  project. ``ENVELOPE_SUBJECT_INTRO`` goes after the global prefix and is
  followed by the actual subject entered in the form by website's user.
  
  Default value: *Message from contact form:*

* ``ENVELOPE_RECIPIENTS_BY_CATEGORY``: Allows for the email recipients
  to be determined by the category selected by the user. If this is
  set the True. You will want to set your
  ``ENVELOPE_EMAIL_RECIPIENTS`` like so::

    ENVELOPE_EMAIL_RECIPIENTS = {
        'category_id': ['example@example.com', 'example2@example.com'],
    }

  Now it should send based on the category selected by the user. This
  is useful if you have different groups handling different requests.
