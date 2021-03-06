This program integrates with service-map: https://github.com/mozilla/service-map
It posts a JSON version of the Gdocs RRA documents to service-map, to be precise.

See also: https://wiki.mozilla.org/Security/Risk_management/Rapid_Risk_Assessment

Get oauth2 credentials
======================

See http://gspread.readthedocs.org/en/latest/oauth2.html for a guided version of this.

As your user, login to https://console.developers.google.com/project/ and create a new project.
Go to "API&Auth/APIs".
Give that project API rights for the Drive API.
Go to "API&Auth/Credentials".
Click "Create client ID" as "Service ID".
You'll get a JSON key back (JWT), that's your credentials.


.. note::

	Make sure you authorize your Service email to all the spreadsheets you'll want to have access to! By default it
has no accesses.

JSON Format
===========

See the file rra2json.inc.json that is included for the exact and complete format. Here's an approximation of what
you'll get though:

  ::

  {
  'source': '1deadbeef-Mju0niB5gZaxy5uZ24_kuJiN6wOSyIx3JJRAyks',
  'timestamp': '2015-05-11T15:50:13.185754+00:00',
  'summary': 'RRA for <something>',
  'tags': ['RRA', 'service', '1.0.0'],
  'severity': 'INFO',
  'lastmodified': '2015-05-09T01:18:55.850000+00:00',
  'category': 'rra_data',
  'details': {
        'risk': {
                'availability': {
                        'reputation':   {'impact': 'Unknown', 'probability': ''},
                        'finances':     {'impact': 'Unknown', 'probability': ''},
                        'productivity': {'impact': 'Unknown', 'probability': ''}
                },
                'integrity': {
                        'reputation':   {'impact': 'Unknown', 'probability': ''},
                        'finances':     {'impact': 'Unknown', 'probability': ''},
                        'productivity': {'impact': 'Unknown', 'probability': ''}
                },
                'confidentiality': {
                        'reputation':   {'impact': 'Unknown', 'probability': ''},
                        'finances':     {'impact': 'Unknown', 'probability': ''},
                        'productivity': {'impact': 'Unknown', 'probability': ''}
                },
        'metadata': {
                'service': '<something>',
                'owner': 'IT Team, J.Doe',
                'description': 'A service to do <something>',
                'developer': 'Dev Team, J.Doe',
                'operator': 'IT Team, J.Doe',
                'RRA_version': '2.5.0',
                'scope': 'The <something> part of the <something service>'
        },
        'data': {
                'Unknown': [],
                'PUBLIC': [],
                'INTERNAL': [],
                'SECRET': [],
                'RESTRICTED': [],
                'default': ''
        }
  }

