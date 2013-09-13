function home()
{
    return isset($_SESSION['user_logged_in']) ? '
<<<<<<< HEAD
    <p>
      Hello, ' . $_SESSION['user_name'] . '. You are now logged in. Try to close
      this browser tab and open it again. Still logged in! ;)
    </p>
    <p>
      <a class="btn" href="?a=logout">Logout</a>
    </p>' : login_form();
=======
<p>
Hello, ' . $_SESSION['user_name'] . '. You are now logged in. Try to close
this browser tab and open it again. Still logged in! ;)
</p>
<p>
<a class="btn" href="?a=logout">Logout</a>
</p>' : login_form();
>>>>>>> 582a9cc985a420c963d63e935e2aeb32ca2ab051
}

function logout()
{
    $_SESSION = array();
    $_SESSION['msg'] = "You are now logged out";
    header('Location: ' . $_SERVER['PHP_SELF']);
    exit(); // TODO: should we really use exit() ?
}

function login()
{
    if (!empty($_POST)) {
        $msg = '';
        $user = read_user($_POST['user_name']);
        if (isset($user['user_name'])) {
            if (password_verify($_POST['user_password'], $user['user_password_hash'])) {
                create_session($user);
                header('Location: ' . $_SERVER['PHP_SELF']);
                exit();
            } else $msg = 'Wrong password';
        } else $msg = 'User does not exist';
        $_SESSION['msg'] = $msg;
    }
    return login_form();
}

function register()
{
    if (!empty($_POST)) {
        $msg = '';
        if ($_POST['user_name']) {
            if ($_POST['user_password_new']) {
                if ($_POST['user_password_new'] === $_POST['user_password_repeat']) {
                    if (strlen($_POST['user_password_new']) > 5) {
                        if (strlen($_POST['user_name']) < 65 && strlen($_POST['user_name']) > 1) {
                            if (preg_match('/^[a-z\d]{2,64}$/i', $_POST['user_name'])) {
                                $user = read_user($_POST['user_name']);
                                if (!isset($user['user_name'])) {
                                    if ($_POST['user_email']) {
                                        if (strlen($_POST['user_email']) < 65) {
                                            if (filter_var($_POST['user_email'], FILTER_VALIDATE_EMAIL)) {
                                                create_user();
                                                $_SESSION['msg'] = 'You are now registered so please login';
                                                header('Location: ' . $_SERVER['PHP_SELF']);
                                                exit();
                                            } else $msg = 'You must provide a valid email address';
                                        } else $msg = 'Email must be less than 64 characters';
                                    } else $msg = 'Email cannot be empty';
                                } else $msg = 'Username already exists';
                            } else $msg = 'Username must be only a-z, A-Z, 0-9';
                        } else $msg = 'Username must be between 2 and 64 characters';
                    } else $msg = 'Password must be at least 6 characters';
                } else $msg = 'Passwords do not match';
            } else $msg = 'Empty Password';
        } else $msg = 'Empty Username';
        $_SESSION['msg'] = $msg;
    }
    return register_form();
}

<<<<<<< HEAD

//REVIEW BY CLASSMATE
//The way He/She structured the code is good. He/She used appropiate names for the function,
//which helps us know what the code is about and what is going to do. He/She should of used
//comments to help a bit more on what the next set of codes is and what it does.
//It looks like it's letting the user register for an account.

//Joshua Peralta
=======
>>>>>>> 582a9cc985a420c963d63e935e2aeb32ca2ab051
