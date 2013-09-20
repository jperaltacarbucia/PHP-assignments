## Homework 5.1: Starting to understand more complex French

* Login to Github and approve my pull request to get the file `homework-5.1.md` in your `assignments` repository.
* Log into Cloud9 and use `git pull` to get the file into your workspace.
 
* Find [the Wordpress project on Github][wordpress], fork it into your own account, and clone it into a Cloud9 workspace.
* Open your Wordpress workspace and find a file that has some branching _if-then-else_ logic; look for some juicy conditionals and guard clauses.
* Copy-paste your examples into `homework-5.1.md` (this file) and attempt to identify the conditions with comments like so:
> USERNAME/Wordpress/path/to/file.php:00
> ```php
>   if ( $mom_says == 'yes' ) // if mom says yes
> ```

* Save your file locally, add and commit it with git, and push your changes to your Github account.
* **Bonus points**: open a pull request back to the original repo with your work to date.

[wordpress]:https://github.com/Wordpress/Wordpress/


if ( ! comments_open( $comment_post_ID ) ) {
	/**
	 * Fires when a comment is attempted on a post that has comments closed.
	 *
	 * @since unknown
	 * @param int $comment_post_ID Post ID.
	 */
	do_action( 'comment_closed', $comment_post_ID );
	wp_die( __('Sorry, comments are closed for this item.') );
} elseif ( 'trash' == $status ) {
	/**
	 * Fires when a comment is attempted on a trashed post.
	 *
	 * @since 2.9.0
	 * @param int $comment_post_ID Post ID.
	 */
	do_action( 'comment_on_trash', $comment_post_ID );
	exit;
} elseif ( ! $status_obj->public && ! $status_obj->private ) {
	/**
	 * Fires when a comment is attempted on a post in draft mode.
	 *
	 * @since unknown
	 * @param int $comment_post_ID Post ID.
	 */
	do_action( 'comment_on_draft', $comment_post_ID );
	exit;
} elseif ( post_password_required( $comment_post_ID ) ) {
	/**
	 * Fires when a comment is attempted on a password-protected post.
	 *
	 * @since unknown
	 * @param int $comment_post_ID Post ID.
	 */
	do_action( 'comment_on_password_protected', $comment_post_ID );
	exit;
} else {
	/**
	 * Fires before a comment is posted.
	 *
	 * @since unknown
	 * @param int $comment_post_ID Post ID.
	 */
	do_action( 'pre_comment_on_post', $comment_post_ID );
}

$comment_author       = ( isset($_POST['author']) )  ? trim(strip_tags($_POST['author'])) : null;
$comment_author_email = ( isset($_POST['email']) )   ? trim($_POST['email']) : null;
$comment_author_url   = ( isset($_POST['url']) )     ? trim($_POST['url']) : null;
$comment_content      = ( isset($_POST['comment']) ) ? trim($_POST['comment']) : null;

// If the user is logged in
$user = wp_get_current_user();
if ( $user->exists() ) {
	if ( empty( $user->display_name ) )
		$user->display_name=$user->user_login;
	$comment_author       = wp_slash( $user->display_name );
	$comment_author_email = wp_slash( $user->user_email );
	$comment_author_url   = wp_slash( $user->user_url );
	if ( current_user_can( 'unfiltered_html' ) ) {
		if ( ! isset( $_POST['_wp_unfiltered_html_comment'] )
			|| ! wp_verify_nonce( $_POST['_wp_unfiltered_html_comment'], 'unfiltered-html-comment_' . $comment_post_ID )
		) {
			kses_remove_filters(); // start with a clean slate
			kses_init_filters(); // set up the filters
		}
	}
} else {
	if ( get_option('comment_registration') || 'private' == $status )
		wp_die( __('Sorry, you must be logged in to post a comment.') );
}



//If a comment is posted on a closed comment section, Take action if is closed
    //closed: comment is closed, send message comments is closed. then exit
//elseif comment is posted on trash, take action: comment on trash then exit
//elseif comment is posted on public comment section, while being private, take action: comment on draft, then exit
//elseif password is required, take action: comment on password protected,then exit
//else sends it before comment is posted, take action: pre-comment on post, then exit
