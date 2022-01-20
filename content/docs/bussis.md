

# 线上模型特征
select
    body["user_id"] user_id,
    get_json_object(body['feature_original'],'$.apply_ts') apply_ts,
    get_json_object(body['feature_original'],'$.age') age,
    get_json_object(body['feature_original'],'$.city') city,
    get_json_object(body['feature_original'],'$.device') device,
    get_json_object(body['feature_original'],'$.apply_ch') apply_ch,
    get_json_object(body['feature_original'],'$.lead_chl') lead_chl,
    get_json_object(body['feature_original'],'$.feeexpect') feeexpect,
    get_json_object(body['feature_original'],'$.friendchildrenstatus') friendchildrenstatus,
    get_json_object(body['feature_original'],'$.gender') gender,
    get_json_object(body['feature_original'],'$.regtype') regtype,
    get_json_object(body['feature_original'],'$.source') source,
    get_json_object(body['feature_original'],'$.cur_be_follow_cnt') cur_be_follow_cnt,
    get_json_object(body['feature_original'],'$.cur_follow_cnt') cur_follow_cnt,
    get_json_object(body['feature_original'],'$.cur_friend_cnt') cur_friend_cnt,
    get_json_object(body['feature_original'],'$.total_listen_success') total_listen_success,
    get_json_object(body['feature_original'],'$.cur_class_cnt') cur_class_cnt,
    get_json_object(body['feature_original'],'$.total30_listen_success') total30_listen_success,
    get_json_object(body['feature_original'],'$.total_tv_finish') total_tv_finish,
    get_json_object(body['feature_original'],'$.cur_bind_wechat') cur_bind_wechat,
    get_json_object(body['feature_original'],'$.total_live_honor') total_live_honor,
    get_json_object(body['feature_original'],'$.total30_join_class') total30_join_class,
    get_json_object(body['feature_original'],'$.cur_vip_is') cur_vip_is,
    get_json_object(body['feature_original'],'$.is_bought_ohb') is_bought_ohb,
    get_json_object(body['feature_original'],'$.is_pay') is_pay,
    get_json_object(body['feature_original'],'$.is_friend_introduce') is_friend_introduce,
    get_json_object(body['feature_original'],'$.is_bought_read') is_bought_read,
    get_json_object(body['feature_original'],'$.device_model') device_model,
    get_json_object(body['feature_original'],'$.total_apply_people') total_apply_people,
    get_json_object(body['feature_original'],'$.first_apply_time') first_apply_ts,
    body['model_name'] model_name,
    body['score'] score,
    get_json_object(body['feature_original'],'$.agelevel') level,
    get_json_object(body['feature_original'],'$.reg_ts') reg_ts,
    get_json_object(body['feature_original'],'$.birthday') birthday,
    get_json_object(body['feature_original'],'$.province') province,
    get_json_object(body['feature_original'],'$.search_start_time') search_start_time,
    get_json_object(body['feature_original'],'$.search_start_cnt') search_start_cnt,
    get_json_object(body['feature_original'],'$.search_start_organ') search_start_organ,
    get_json_object(body['feature_original'],'$.search_eng_capacity') search_eng_capacity,
    body['recommend'] recommend,
    get_json_object(body['feature_original'],'$.sale_id') sale_id,
    body['sublevel'] sublevel,
    body['server_start'] server_start,
    body['server_ts'] server_ts
    from
        dwd.dwd_h_log_pub_sale_statlog_i 
    where 
        p_day ='20211215' and service ='airecommendproxy' and msg='userleadslevel.RealTimeProxy' 





-- 少儿leads宽表 dws.dws_d_cus_pub_leads_taget_f
--绘本宽表 dws.dws_d_cus_pic_user_detail_f
--用户行为数据 dws.dws_d_log_pub_user_start_visit_i
--用户180天行为数据 ads.ads_d_use_pic_180_total_bhv_f
--用户申请试听表 dwd.dwd_d_use_eng_apply_audition_log_i


用户实时特征打分 
背景绘本实时特征转化率高，离线特征转化率低，低一个点
对用户行为按经验值，标记权重打分，
用户登陆时，计算
