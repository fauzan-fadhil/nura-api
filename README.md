# nura-api
'use strict';

exports.ok = function (values, res) {
    var code = 200;
    var desc = "Valid";

    //if empty, mean no user found
    if (values == "") {
        code = 909;
        desc = 'Wrong username and password!'
    }

    var data = {
        'status': code,
        'description': desc,
        'values': values
    };

    res.json(data);
    res.end();
};

exports.submit = function (values, res) {
    var code = 200;
    var desc = "Success";

    //if empty, mean no user found
    if (values == "") {
        code = 909;
        desc = 'Failure'
    }

    var data = {
        'status': code,
        'description': desc,
        'values': values
    };

    res.json(data);
    res.end();
}

exports.encrypted = function (values, res) {
    var data = {
        'status': 13,
        'description': "Encrypted",
        'values': values
    };

    res.json(data);
    res.end();
};

exports.validate = function (values, res) {
    var data = {};

    //if empty, mean no user found
    if (values == "") {
        data = {
            'status': 909,
            'description': 'Wrong username and password!'
        };
    } else {
        data = {
            'status': 200,
            'description': "Successfully logged in",
            'places_id': values[0].places_id,
            'adminpos_id': values[0].adminpos_id,
            'full_name': values[0].full_name,
            // 'values': values
        };
    }

    // console.log(values);

    res.json(data);
    res.end();
};
