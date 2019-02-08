Test input data format for social rates algorithm

Content table:
- content_id - numeric or text - doesn't matter
- timestamp - iso format "2019-02-07T09:29:03.714Z"
- content_type - post, comment, repost etc., plain text or a key from the dictionary
- account_id - author id, numeric or text
- parent_content_id - parent id for comment or repost

Interactions table:
- timestamp
- interaction_type - like, upvote etc., plain text or a key from the dictionary
- account_id
- content_id

Table format is csv with ';' for delimeter
