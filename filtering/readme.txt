[x] create a gaussian / box filter
[x] filter the image with a given filter.
[x] test these filters at different sizes and analyze their effects on the stop sign image.
    - show output with gaussian, varying size and sigma
    - show output with box, varying size

[x] create an edge filter and filter the image.
can you reliably detect edges?
create your own edge detector from scratch – do your best to create a good edge detector.

[o] think of a filter that will respond strongly on the stop sign only.
create it and filter the image.
analyze the results and improve your filter to detect as well as possible the sign by using your filter.
the goal is to automatically draw a bounding box just around the stop sign (and not around other regions in the images).
    [o] diff orientations
    [x] multi-scale


- sigma effect, cv2.matchTemplate

# attempts
- using color info - strided conv with a large box filter -> get local color clusters
- keep tpl fixed, resize the image


# tpl = cv2.resize(tpl_edges, None, fx=0.6, fy=0.6)
# best_loc, br, r = None, None, None
# best_val = -np.inf
#
# th, tw = tpl.shape[:2]
#
# for i in [1.4, 1.2, 1.0, 0.8, 0.6, 0.4]:
# 	img = cv2.resize(img_edges, None, fx=i, fy=i)
# 	print(img.shape)
#
# 	res = cv2.matchTemplate(img, tpl, cv2.TM_CCOEFF)
# 	_, max_val, _, max_loc = cv2.minMaxLoc(res)
#
# 	if max_val > best_val:
# 		best_val = max_val
# 		best_loc = max_loc
# 		r = i
#
# top = (int(r * best_loc[0]), int(r * best_loc[1]))
# bot = (int((best_loc[0] + tw) * r), int((best_loc[1] + th) * r))
# return top, bot
